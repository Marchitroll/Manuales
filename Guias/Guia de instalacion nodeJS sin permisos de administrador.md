# Node JS (sin permisos de administrador)

En caso de que no tengamos acceso a los privilegios de administrador, aún así podemos instalar Node.js

## Antes de instalar

Antes de instalar **Node.js (sin privilegios de administrador)** debemos tener en cuenta lo siguiente:

1. Tener instalado VS Code.
2. Tener un programa de compresión/descompresión (como [7zip](https://7-zip.org/)).

## 1. Descargar el archivo

Debemos dirigirnos a la página oficial de [Node.js](https://nodejs.org/). 

En la página principal de Node.js, encontraremos un botón que dice `Download Node.js (LTS)`. Al hacer clic en este botón, descargaremos una versión estable del programa en formato ejecutable. Si deseamos acceder a la última versión disponible y que no sea ejecutable, debemos hacer clic en la sección de [**Download**](https://nodejs.org/en/download).

![paso 1.1](/imagenes/nodejs1-1.png)

Cuando accedamos a la página, nos dirigiremos a la sección de `Prebuilt Binaries` y elegiremos la última versión disponible, que en este ejemplo es la **22.1.0**. El archivo que se descargará será un archivo comprimido.

![paso 1.2](/imagenes/nodejsSinAdministrador.png)

## 2. Descomprimir el archivo

Descomprimimos el archivo descargado, el cual tendrá un nombre parecido a `node-v22.1.0-win-x64.zip`.

Una vez completada la descompresión, se generará una carpeta con el mismo nombre. Al ingresar a esta carpeta, nos encontraremos con los siguientes archivos:

![paso 2.1](/imagenes/nodejsSinAdministrador2.png)

## 3. (Opcional) Mover la carpeta

Opcionalmente, podemos trasladar la carpeta a una ubicación de fácil acceso, siendo recomendable moverla al ``disco local C``.

## 4. Agregar la ruta al PATH

Actualmente, si abrimos una terminal y escribimos:

    node -v

nos aparecerá el siguiente mensaje:

![paso 4.1](/imagenes/nodejsSinAdministrador3.png)

Para solucionar este problema debemos agregar la ruta de nuestra carpeta que contiene a Node.js al PATH, que es una [variable de entorno](https://www.genbeta.com/desarrollo/variables-entorno-que-sirven-como-podemos-editarlas-windows-linux).

Primero, debemos copiar la ruta de nuestro directorio. Para ello, nos dirigimos a la carpeta que descomprimimos y copiamos la dirección que aparece en la barra de direcciones.

![paso 4.1.1](/imagenes/nodejsSinAdministrador3-1.png)

Ahora, buscamos la palabra **`variables`** en el menú de inicio. Podrán notar que aparecerán varias opciones. La que debemos elegir es `"Editar variables de entorno de esta cuenta"`.

![paso 4.2](/imagenes/nodejsSinAdministrador4.png)

Al darle clic o "enter" nos abrirá la siguiente ventana:

![paso 4.3](/imagenes/nodejsSinAdministrador5.png)

Buscamos la variable de nombre `Path` y hacemos clic en donde dice `Editar...`

![paso 4.4](/imagenes/nodejsSinAdministrador6.png)

Al abrirse la nueva ventana, haremos clic en la opción `Nuevo` y pegaremos la ruta que copiamos anteriormente.

![paso 4.5](/imagenes/nodejsSinAdministrador7.png)

Damos clic en `Aceptar` (dos veces para cerrar ambas ventanas emergentes) y luego volvemos a intentar el comando en una terminal.

![paso 4.6](/imagenes/nodejsSinAdministrador8.png)

Como se puede notar, ahora el programa está detectado. Con esto, Node.js está instalado sin necesidad de tener privilegios de administrador.

