# React 

React es una biblioteca de JavaScript utilizada para construir interfaces de usuario interactivas y dinámicas en aplicaciones web. Permite a los desarrolladores crear componentes reutilizables que actualizan automáticamente la interfaz cuando los datos cambian, lo que facilita la construcción de aplicaciones de una sola página y aplicaciones web complejas de manera más eficiente.

Por otro lado, Create-React-App facilita el inicio rápido del desarrollo de aplicaciones web con React, sin la necesidad de lidiar con la configuración inicial del proyecto. Es la manera ideal de comenzar a construir una nueva aplicación de página única con React.

Para más detalles sobre esta herramienta, puedes consultar la [página oficial de React (en su versión legacy)](https://es.legacy.reactjs.org/docs/create-a-new-react-app.html) y el [repositorio en GitHub](https://github.com/facebook/create-react-app).

## Requisitos previos

Antes de crear nuestra aplicación debemos tener lo siguiente:

1. VS Code.
2. [Node.js](Guia%20de%20instalacion%20nodeJS.md)

## 1. Preparar el entorno

Lo primero que debemos hacer es definir dónde vamos a guardar nuestro proyecto, para ello lo recomendables es crear una carpeta. En este tutorial la carpeta se llamará `Proyecto con React` y se ubicará en el `disco local C`.

Abrimos una terminal y desde allí nos dirigimos a la ruta de nuestra carpeta, que en este caso es `C:\Proyecto con React`. El comando que usaremos será el siguiente: 

    cd "[ruta de la carpeta]"

![](/imagenes/appConReact1.png)

## 2. Crear el proyecto

Una vez dentro, creemos la app con el siguiente comando:

    npx create-react-app [nombre-del-proyecto]

Si quieres saber más acerca de **npx**, pulsa [aquí](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b)

Si aparece un error parecido a este: [(pulsa aquí)](/Guias/Solución%20al%20error%20de%20Politicas%20de%20ejecucion.md)

![](/imagenes/politicasEjecucion1.png)

Si aparece un error parecido a este: [(pulsa aqui)](/Guias/Solución%20al%20error%20de%20no%20encontrar%20npx.md)

![](/imagenes/errorNPXnoEncontrado1.png)

Si no hay errores, este proceso nos pedirá una confirmación. La aceptaremos y procederá a la creación del proyecto con React. El resultado debería ser similar al siguiente:

![](/imagenes/appConReact2.png)

## 3. Abrir el proyecto

Como última paso, encontraremos la app creada dentro de la carpeta que creamos al inicio. 

![](/imagenes/appConReact3.png)

Entonces procederemos a abrir esa carpeta en VS Code y así podremos comenzar a desarrollar nuestra aplicación.

Para lanzar la aplicación de manera local, necesitaremos ejecutar el siguiente comando en la terminal (asegúrate de estar ubicado dentro de la carpeta de nuestro proyecto, de lo contrario, obtendremos un error):

    npm start

Todos los demás comandos estarán disponibles dentro del archivo **"README.md"** ubicado dentro del proyecto.

![](/imagenes/appConReact4.png)