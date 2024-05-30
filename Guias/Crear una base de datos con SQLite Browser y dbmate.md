# SQLite Browser

**SQLite Browser** (DB Browser for SQLite) es una herramienta gráfica de código abierto diseñada para facilitar la gestión de bases de datos SQLite. Permite a los usuarios crear, diseñar, editar y visualizar bases de datos de manera intuitiva a través de una interfaz visual, sin necesidad de escribir comandos SQL directamente.

# DBmate

**DBmate** es una herramienta de migración de bases de datos de código abierto escrita en Go, diseñada para simplificar el manejo de migraciones en diversos sistemas de bases de datos, incluyendo SQLite, MySQL, PostgreSQL y ClickHouse. Facilita la creación, aplicación y reversión de migraciones de base de datos a través de una línea de comandos sencilla y eficiente.

## Requisitos previos

Para crear nuestra base de datos debemos tener lo siguiente:

1. VSCode
2. [SQLite browser](https://sqlitebrowser.org/)
3. [NodeJS](/Guias/Guia%20de%20instalacion%20nodeJS.md)

## 1. Preparar el entorno

Para comenzar, es necesario crear una carpeta donde se almacenarán nuestros archivos. En este tutorial, denominaremos a la carpeta como `prueba-bd`.

## 2. Crear el proyecto

Abre una terminal y navega hasta la ubicación de tu carpeta utilizando la línea de comandos. Una vez allí, ejecuta el siguiente comando:

```bash
npm init -y
```

Esto generará un archivo llamado `package.json` con una estructura similar a esta:

```json
{
  "name": "prueba-bd",
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

## 3. Instalar dbmate y SQLite3 como dependencias

El siguiente paso consiste en instalar dbmate y SQLite como una dependencia dentro del archivo `package.json`. Para lograrlo, ejecuta el siguiente comando en tu terminal:

    npm install dbmate --save

    npm install sqlite3 --save

El resultado esperado incluye la creación de dos nuevos archivos:

- La carpeta `node_modules`.
- El archivo `package-lock.json`.

Asimismo, nuestro archivo `package.json` será actualizado y tendrá una estructura similar a esta:

```json
{
  "name": "prueba-bd",
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
    "dbmate": "^2.16.0",
    "sqlite3": "^5.1.7"
  }
}
```

Como puedes ver, hemos agregado dbmate y SQLite como dependencias en nuestro archivo.

## 4. Crear el archivo `.env`

En el directorio que estamos trabajando, crearemos un archivo `.env` en el que escribiremos la siguiente línea:

``` env
DB=sqlite:db/app.db
```
## 5. Creación de scripts

Dentro del `package.json` deberemos agregar los 3 siguientes scripts que nos evitarán escribir comandos de más:


```json
"dbmate:new": "npx dbmate -d \"db/migrations\" -e \"DB\" new ",
"dbmate:up": "npx dbmate -d \"db/migrations\" -e \"DB\" up",
"dbmate:rollback": "npx dbmate -d \"db/migrations\" -e \"DB\" rollback"
```

Nuestro `package.json` debería quedar así:

```json
{
  "name": "prueba-bd",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dbmate:new": "npx dbmate -d \"db/migrations\" -e \"DB\" new ",
    "dbmate:up": "npx dbmate -d \"db/migrations\" -e \"DB\" up",
    "dbmate:rollback": "npx dbmate -d \"db/migrations\" -e \"DB\" rollback"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": "",
  "dependencies": {
    "dbmate": "^2.16.0",
    "sqlite3": "^5.1.7"
  }
}

```

## 6. Creación de migraciones nuevas

Para crear migraciones nuevas debemos usar el siguiente comando en la terminal:

    npm run dbmate:new [nombre]

Cuando lo ejecutemos por primera vez, se creará una carpeta llamada `db` y dentro de esta, otra carpeta llamada `migrations`. Dentro de la carpeta `migrations`, se generará nuestra migración. En ejecuciones posteriores, la nueva migración se creará en la misma ruta (`\db\migrations`).

Es imprescindible editar la migración. En la sección 'up' se incluirá la creación de la tabla o cualquier adición/edición de datos necesaria, mientras que en la sección 'down' se colocará el comando contrario a 'up' (por ejemplo: `DROP TABLE [nombre];`).

### Ejemplo de creación de tabla

Podemos guiarnos de esta plantilla para crear tablas:

```sql
-- Para entidades fuertes
CREATE TABLE fuertes (
    id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
    nombre VARCHAR(20) NOT NULL
);

-- Para entidades débiles
CREATE TABLE debiles (
    id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
    inicio DATETIME NOT NULL,
    fin DATE,
    titulo_distribucion VARCHAR(40) NOT NULL,
    titulo_original VARCHAR(40) NOT NULL,
    anio_produccion INTEGER NOT NULL,
    horas INTEGER NOT NULL,
    fuerte_id INTEGER,
    FOREIGN KEY(fuerte_id) REFERENCES fuertes(id) ON DELETE CASCADE
);

```

En este caso, ejecutaré el siguiente comando para crear una tabla de paises:

    npm run dbmate:new mi-primera-tabla

Accederé a la migración recién creada y escribiré el siguiente código SQL para crear la tabla de países:

```SQL
-- migrate:up

CREATE TABLE paises (
  id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
  nombre VARCHAR(40) NOT NULL,
  bandera_url VARCHAR(100) NOT NULL,
  gentilicio VARCHAR(30) NOT NULL
);

-- migrate:down

DROP TABLE paises;

```
Esta es una tabla vacía, por lo que ahora crearé una migración para llenar los datos:

    npm run dbmate:new llenar-tabla

En esa migración escribiré el siguiente código SQL que me permitirá llena la tabla de países:

```SQL
-- migrate:up

INSERT INTO paises (id, nombre, bandera_url, gentilicio) VALUES
(1, 'Estados Unidos de América', 'https://upload.wikimedia.org/wikipedia/en/a/a4/Flag_of_the_United_States.svg', 'Estadounidense'),
(2, 'Canadá', 'https://upload.wikimedia.org/wikipedia/commons/c/cf/Flag_of_Canada.svg', 'Canadiense'),
(3, 'Brasil', 'https://upload.wikimedia.org/wikipedia/en/0/05/Flag_of_Brazil.svg', 'Brasileño'),
(4, 'Reino Unido', 'https://upload.wikimedia.org/wikipedia/en/a/ae/Flag_of_the_United_Kingdom.svg', 'Británico'),
(5, 'Alemania', 'https://upload.wikimedia.org/wikipedia/en/b/ba/Flag_of_Germany.svg', 'Alemán'),
(6, 'Francia', 'https://upload.wikimedia.org/wikipedia/en/c/c3/Flag_of_France.svg', 'Francés'),
(7, 'Italia', 'https://upload.wikimedia.org/wikipedia/en/0/03/Flag_of_Italy.svg', 'Italiano'),
(8, 'España', 'https://upload.wikimedia.org/wikipedia/en/9/9a/Flag_of_Spain.svg', 'Español'),
(9, 'China', 'https://upload.wikimedia.org/wikipedia/commons/f/fa/Flag_of_the_People%27s_Republic_of_China.svg', 'Chino'),
(10, 'Japón', 'https://upload.wikimedia.org/wikipedia/en/9/9e/Flag_of_Japan.svg', 'Japonés'),
(11, 'India', 'https://upload.wikimedia.org/wikipedia/en/4/41/Flag_of_India.svg', 'Indio'),
(12, 'Rusia', 'https://upload.wikimedia.org/wikipedia/en/f/f3/Flag_of_Russia.svg', 'Ruso'),
(13, 'Australia', 'https://upload.wikimedia.org/wikipedia/commons/b/b9/Flag_of_Australia.svg', 'Australiano'),
(14, 'Sudáfrica', 'https://upload.wikimedia.org/wikipedia/commons/a/af/Flag_of_South_Africa.svg', 'Sudafricano'),
(15, 'México', 'https://upload.wikimedia.org/wikipedia/commons/f/fc/Flag_of_Mexico.svg', 'Mexicano'),
(16, 'Argentina', 'https://upload.wikimedia.org/wikipedia/commons/1/1a/Flag_of_Argentina.svg', 'Argentino'),
(17, 'Nigeria', 'https://upload.wikimedia.org/wikipedia/commons/7/79/Flag_of_Nigeria.svg', 'Nigeriano'),
(18, 'Arabia Saudita', 'https://upload.wikimedia.org/wikipedia/commons/0/0d/Flag_of_Saudi_Arabia.svg', 'Saudita'),
(19, 'Egipto', 'https://upload.wikimedia.org/wikipedia/commons/f/fe/Flag_of_Egypt.svg', 'Egipcio'),
(20, 'Colombia', 'https://upload.wikimedia.org/wikipedia/commons/2/21/Flag_of_Colombia.svg', 'Colombiano');

-- migrate:down

DELETE FROM paises;

```

## 7. Creación de la base de datos

Una vez hallamos creado nuestras migraciones, lo que debemos hacer es ponerlas en una base de datos, para ello nos ayudaremos del siguiente comando:

    npm run dbmate:up

Una vez ejecutado el proceso por primera vez, se creará una base de datos llamada `app.db` dentro de la carpeta `db`. En ejecuciones posteriores, solo se aplicarán las nuevas migraciones a esa misma base de datos, asegurando la consistencia de los datos y la estructura. Con esto, habremos creado nuestra base de datos, y podremos visualizarla a través de SQLite Browser.

### Siguiendo con el ejemplo anterior...

Ahora procederemos a crear nuestra base de datos. Por lo que ejecutaremos el siguiente comando

    npm run dbmate:up

Y automáticamente se nos creará la base de datos. Como se aprecia en la imagen de abajo, podemos ver los datos dentro de SQLite browser

![](/imagenes/SQLite%20Browser%20ejemplo.png)

## Deshacer cambios

Si cometes un error en algún momento, puedes revertir el último cambio realizado a través de la sección `-- migrate:down` dentro de tus migraciones. Este actúa como un "control + z", deshaciendo el último cambio y restaurando la base de datos al estado anterior. Para ejecutar dicha acción, escribe el siguiente comando:

    npm run dbmate:rollback

## Mayor información

Si deseas acceder a mayor información te recomiendo acceder a las siguientes páginas:

[Documentación de SQLite Browser](https://github.com/sqlitebrowser/sqlitebrowser/wiki)

[Repositorio oficial de dbmate](https://github.com/amacneil/dbmate)