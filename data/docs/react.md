- #frontend | #react

# Contexto
- **React** es una librería de *JavaScript* (no un *framework*) creada por **Meta (Facebook)** para construir interfaces de usuario de manera más rápida, modular y eficiente.
- Su idea principal es muy sencilla:
	- En lugar de manipular manualmente el **DOM** (lo que ves en el navegador) cada vez que algo cambia,
	- **React** crea una versión virtual de la página (**Virtual DOM**) y solo actualiza las partes que cambian, haciéndolo más rápido y más organizado.
- El componente principal es **App**. Debajo de este se pueden crear múltiples componentes como (navegación, *links*, etc).

# Estructura 
```
mi-proyecto/
│
├── public/
│   └── index.html         <-- Archivo HTML base
│
├── src/                   <-- Todo tu código de React
│   ├── assets/            <-- Imágenes, íconos, fuentes, etc.
│   ├── components/        <-- Componentes pequeños y reutilizables
│   │   └── Boton.jsx
│   ├── pages/             <-- Páginas completas (Home, About, Contact, etc.)
│   │   └── Home.jsx
│   ├── App.jsx            <-- Componente raíz
│   ├── main.jsx           <-- Punto de entrada de la aplicación
│   └── styles/            <-- CSS o archivos de estilos
│       └── App.css
│
├── package.json           <-- Configuración del proyecto (dependencias, scripts, etc.)
├── vite.config.js         <-- (opcional si usas Vite) Configuración del build
├── .gitignore             <-- Archivos a ignorar en git
└── README.md              <-- Explicación del proyecto
```