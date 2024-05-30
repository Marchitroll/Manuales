# Express js

Express.js es un framework web para Node.js, diseñado para facilitar la creación y gestión de aplicaciones web y API. Ofrece una serie de herramientas y utilidades que simplifican el proceso de desarrollo al proporcionar una estructura y componentes predefinidos para manejar las peticiones y respuestas HTTP, entre otras funcionalidades.

## Requisitos previos

Antes de crear nuestra aplicación debemos tener lo siguiente:

1. VS Code.
2. [Node.js](Guia%20de%20instalacion%20nodeJS.md)

## 1. Preparar el entorno

Para empezar, debemos crear una carpeta donde se guardarán nuestros archivos. En este tutorial, la carpeta tendrá el nombre de `prueba-server`

## 2. Crear el proyecto

Abre una terminal y navega hasta la ubicación de tu carpeta utilizando la línea de comandos. Una vez allí, introduce el siguiente comando:

    npm init -y

Esto nos creará un archivo llamado `package.json` que tendrá una estructura similar a esta:

```json
{
  "name": "prueba-server",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": ""
}

```

## 3. Instalar express como dependencia

El siguiente paso es instalar express como dependencia dentro del archivo `package.json`. Para ello, ejecutaremos el siguiente comando en nuestra terminal:

    npm install express --save

El resultado esperado es que se nos creen 2 ficheros nuevos: 

* La carpeta `node_modules`
* El archivo `package-lock.json`

Asimismo, nuestro archivo `package.json` será actualizado y tendrá una estructura similar a esta:

```json
{
  "name": "prueba-server",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": "",
  "dependencies": {
    "express": "^4.19.2"
  }
}
```

Como puedes observar, hemos añadido Express como una dependencia en nuestro archivo.

## 4. Crear el archivo del servidor

Para proceder, debemos generar el archivo donde nuestro servidor funcionará. Esto implica la creación de un archivo JavaScript con cualquier nombre y la extensión adecuada. En este caso, lo llamaremos `servidor.js`.

## 5. Escribir el código del servidor

El código básico que puede tener cualquier servidor de express es el siguiente:

```js
const express = require('express');
const app = express();
const puerto = 3000;

app.get('/', (req, res) => {
  res.send('¡Hola Mundo!');
});

app.listen(puerto, () => {
  console.log(`La aplicación de ejemplo está escuchando en el puerto ${puerto}`);
});
```

## Abrir el servidor 

Finalmente, para visualizar nuestro servidor, debemos ejecutarlo en una terminal. Para ello, en la misma terminal en la que estábamos trabajando anteriormente y que está ubicada en nuestra carpeta, escribiremos el siguiente comando:

    node servidor.js

Observaremos que la consola imprime el mensaje que especificamos. Ahora que el servidor está en funcionamiento, para acceder a nuestra única ruta creada (endpoint), debemos dirigirnos a la siguiente dirección en cualquier navegador:

    localhost:3000

En esa ruta podremos ver nuestro mensaje enviado. Si queremos detener el servidor, podemos hacerlo presionando `control + c` en la terminal.

## Mayor información

Si deseas acceder a mayor información te recomiendo acceder a las siguientes páginas:

[Página oficial de express](https://expressjs.com/)

[Repositorio oficial de express](https://github.com/expressjs/express)

[MDN web docs de express](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction)