- #jwt | #security | #json

# Concepto
- Un **JWT** o *Json Web Token* es un formato compacto y seguro para transmitir información entre dos partes como un objeto *JSON*. Se utiliza para autorización y autenticación.
- Este se guarda localmente en la máquina del usuario, por *cookies* u otra forma. Es una firma que puede validar a ese usuario. 
- Un **JWT** está separado por puntos: `xxxxx.yyyyy.zzzzz`. Se divide en tres partes:
	- *Header*: especifica el tipo de token **JWT** y el algoritmo de firma.
	```json
	{
	  "alg": "HS256",
	  "typ": "JWT"
	}
	```
	- *Payload*: contiene los datos o *claims*, como el *ID* de usuario, roles, tiempo de expiración, etc.
	```json
	{
	  "sub": "1234567890",
	  "name": "Miguel",
	  "iat": 1516239022
	}
	```
	- *Signature*: se genera firmando el *header* y el *payload* codificados en *base64* usando una clave secreta o una clave privada.
	```json
	HMACSHA256(
	  base64UrlEncode(header) + "." + base64UrlEncode(payload),
	  secret
	)
	```