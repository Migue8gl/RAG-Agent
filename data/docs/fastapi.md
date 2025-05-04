- #fastapi | #api | #python

# Security
## Password & Username
- Se puede generar un sistema para comunicar el *frontend* y el *backend* usando [[oauth2]] para construir una autenticación usando *username* y *password*.
```python
from typing import Annotated

from fastapi import Depends, FastAPI
from fastapi.security import OAuth2PasswordBearer

app = FastAPI()

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")


@app.get("/items/")
async def read_items(token: Annotated[str, Depends(oauth2_scheme)]):
    return {"token": token}
```
- El *flow* es el que sigue:
	- El usuario escribe la contraseña y el usuario en el *frontend*.
	- Este manda los datos a una **URL** específica en nuestra [[rest api|API]], en el ejemplo es "token".
	- La **API** comprueba los datos de usuario y contraseña y responde con un *token* para verificar al usuario. Los *tokens* suelen expirar con el tiempo.
	- El *frontend* guarda ese *token* de forma temporal en alguna parte de la máquina del usuario.
	- Cada vez que el usuario utilice otra **URL** de la **API**, se manda una petición con una cabecera *Authorization* con el valor *Bearer* más el *token*.
- *FastAPI* provee herramientas como `OAuthPasswordBearer`, con la cual se puede anclar la **URL** que el usuario utiliza para mandar los datos de usuario y contraseña y que devuelve un *token*. La **URL** del ejemplo es relativa.
- `Depends` es una función de *FastAPI* que permite **inyectar dependencias** automáticamente. En este caso, la dependencia es `oauth2_scheme`. De esta forma se indica que ese parámetro se inyectará por la instancia `oauth2_scheme`. Antes de llamar a la función se llama a la dependencia.
## Get current user
- Dado un *token* de autenticación, es posible crear una dependencia para obtener el usuario al que está asociado el *token*. De esta forma, se crea una función que dependa del sistema de seguridad concreto (en este caso **OAuth**), y esta nueva funcionalidad será inyectada en los [[endpoint|endpoints]] concretos que necesiten decodificar de *token* a usuario concreto. 
- De esta forma es posible obtener datos asociados al usuario (como posibles roles).
```python
from typing import Annotated

from fastapi import Depends, FastAPI
from fastapi.security import OAuth2PasswordBearer
from pydantic import BaseModel

app = FastAPI()

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")


class User(BaseModel):
    username: str
    email: str | None = None
    full_name: str | None = None
    disabled: bool | None = None


def fake_decode_token(token):
    return User(
        username=token + "fakedecoded", email="john@example.com", full_name="John Doe"
    )


async def get_current_user(token: Annotated[str, Depends(oauth2_scheme)]):
    user = fake_decode_token(token)
    return user


@app.get("/users/me")
async def read_users_me(current_user: Annotated[User, Depends(get_current_user)]):
    return current_user
```
- Se puede usar cualquier modelo, base de datos, clase que la aplicación necesite. Gracias al sistema de inyección de dependencia funciona con cualquier sistema.
## JWT + Inyección de dependencias + Hassing
```python
from datetime import datetime, timedelta, timezone
from typing import Annotated

import jwt
from fastapi import Depends, FastAPI, HTTPException, status
from fastapi.security import OAuth2PasswordBearer, OAuth2PasswordRequestForm
from jwt.exceptions import InvalidTokenError
from passlib.context import CryptContext
from pydantic import BaseModel

# to get a string like this run:
# openssl rand -hex 32
SECRET_KEY = "09d25e094faa6ca2556c818166b7a9563b93f7099f6f0f4caa6cf63b88e8d3e7"
ALGORITHM = "HS256"
ACCESS_TOKEN_EXPIRE_MINUTES = 30


fake_users_db = {
    "johndoe": {
        "username": "johndoe",
        "full_name": "John Doe",
        "email": "johndoe@example.com",
        "hashed_password": "$2b$12$EixZaYVK1fsbw1ZfbX3OXePaWxn96p36WQoeG6Lruj3vjPGga31lW",
        "disabled": False,
    }
}


class Token(BaseModel):
    access_token: str
    token_type: str


class TokenData(BaseModel):
    username: str | None = None


class User(BaseModel):
    username: str
    email: str | None = None
    full_name: str | None = None
    disabled: bool | None = None


class UserInDB(User):
    hashed_password: str


pwd_context = CryptContext(schemes=["bcrypt"], deprecated="auto")

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")

app = FastAPI()


def verify_password(plain_password, hashed_password):
    return pwd_context.verify(plain_password, hashed_password)


def get_password_hash(password):
    return pwd_context.hash(password)


def get_user(db, username: str):
    if username in db:
        user_dict = db[username]
        return UserInDB(**user_dict)


def authenticate_user(fake_db, username: str, password: str):
    user = get_user(fake_db, username)
    if not user:
        return False
    if not verify_password(password, user.hashed_password):
        return False
    return user


def create_access_token(data: dict, expires_delta: timedelta | None = None):
    to_encode = data.copy()
    if expires_delta:
        expire = datetime.now(timezone.utc) + expires_delta
    else:
        expire = datetime.now(timezone.utc) + timedelta(minutes=15)
    to_encode.update({"exp": expire})
    encoded_jwt = jwt.encode(to_encode, SECRET_KEY, algorithm=ALGORITHM)
    return encoded_jwt


async def get_current_user(token: Annotated[str, Depends(oauth2_scheme)]):
    credentials_exception = HTTPException(
        status_code=status.HTTP_401_UNAUTHORIZED,
        detail="Could not validate credentials",
        headers={"WWW-Authenticate": "Bearer"},
    )
    try:
        payload = jwt.decode(token, SECRET_KEY, algorithms=[ALGORITHM])
        username = payload.get("sub")
        if username is None:
            raise credentials_exception
        token_data = TokenData(username=username)
    except InvalidTokenError:
        raise credentials_exception
    user = get_user(fake_users_db, username=token_data.username)
    if user is None:
        raise credentials_exception
    return user


async def get_current_active_user(
    current_user: Annotated[User, Depends(get_current_user)],
):
    if current_user.disabled:
        raise HTTPException(status_code=400, detail="Inactive user")
    return current_user


@app.post("/token")
async def login_for_access_token(
    form_data: Annotated[OAuth2PasswordRequestForm, Depends()],
) -> Token:
    user = authenticate_user(fake_users_db, form_data.username, form_data.password)
    if not user:
        raise HTTPException(
            status_code=status.HTTP_401_UNAUTHORIZED,
            detail="Incorrect username or password",
            headers={"WWW-Authenticate": "Bearer"},
        )
    access_token_expires = timedelta(minutes=ACCESS_TOKEN_EXPIRE_MINUTES)
    access_token = create_access_token(
        data={"sub": user.username}, expires_delta=access_token_expires
    )
    return Token(access_token=access_token, token_type="bearer")


@app.get("/users/me/", response_model=User)
async def read_users_me(
    current_user: Annotated[User, Depends(get_current_active_user)],
):
    return current_user


@app.get("/users/me/items/")
async def read_own_items(
    current_user: Annotated[User, Depends(get_current_active_user)],
):
    return [{"item_id": "Foo", "owner": current_user.username}]
```
- El código utiliza [[jwt|JWT]] para generar tokens de acceso seguros. Cuando un usuario se autentica exitosamente en `/token`, se crea un *token* firmado usando una clave secreta (`SECRET_KEY`) y un algoritmo específico (`HS256`). Este *token* incluye un *payload* con el nombre de usuario (`sub`) y un tiempo de expiración (`exp`). La firma digital garantiza la integridad del *token*: cualquier modificación invalidaría la firma. Los *tokens* **JWT** son autocontenidos, lo que permite verificar su validez sin consultar la base de datos en cada petición.
- **FastAPI** aprovecha su sistema de **inyección de dependencias** para gestionar la autenticación de forma modular. La dependencia `oauth2_scheme` (de tipo `OAuth2PasswordBearer`) se encarga de extraer el token de la cabecera `Authorization`. Luego, la función `get_current_user` depende de este esquema para obtener el *token*, decodificarlo usando **JWT**, y validar el usuario contra la base de datos falsa (`fake_users_db`). Esta cadena de dependencias permite reutilizar la lógica de autenticación en múltiples *endpoints* (como `/users/me/` y `/users/me/items/`), asegurando que solo usuarios válidos accedan a los recursos.
- El código utiliza **bcrypt** (a través de `CryptContext` de *Passlib*) para hashear contraseñas de forma segura. Cuando un usuario se registra, `get_password_hash` convierte la contraseña en texto plano a un *hash* irreversible. Durante la autenticación, `verify_password` compara el hash almacenado con el *hash* generado a partir de la contraseña ingresada. Esto previene que las contraseñas reales sean expuestas incluso si la base de datos es comprometida. El uso de *bcrypt* (un algoritmo lento y resistente a fuerza bruta) añade una capa adicional de seguridad contra ataques de diccionario.