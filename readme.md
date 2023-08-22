
# Proyecto Aguacaticos

- Este proyecto ejemplifica la creación de un servidor web dinámico utilizando Node.js. Al combinar varios archivos y módulos, el proyecto demuestra cómo generar contenido personalizado y atractivo en función de las solicitudes del usuario. El objetivo principal es proporcionar una plataforma que presente información sobre productos de manera interactiva y efectiva.

- Mediante el uso de tecnologías como http, url, y slugify, el proyecto destaca la importancia de manejar solicitudes entrantes y presentar respuestas acordes a la URL solicitada. Además, se hace uso de plantillas HTML y un módulo personalizado replaceTemplate.js para garantizar la generación fluida de contenido dinámico.

- La estructura de carpetas y archivos, que incluye la organización de las plantillas, datos de ejemplo en formato JSON y la lógica central del servidor en index.js, permite a los desarrolladores explorar y aprender cómo construir aplicaciones web dinámicas desde cero.

- Este proyecto es ideal tanto para aquellos que están comenzando a familiarizarse con Node.js y el desarrollo web como para aquellos que desean fortalecer sus habilidades en la creación de servidores y la generación de contenido dinámico.

### Estructura de Carpetas

- **dev-data**: Esta carpeta contiene datos de desarrollo que se utilizan para pruebas locales y ajustes.
- **module**: Aquí encontrarás los archivos relacionados con el módulo principal del proyecto.
- **node_modules**: Esta carpeta es generada automáticamente por Node.js y contiene las dependencias del proyecto. No es necesario incluirla en el repositorio.
- **templates**: Contiene las plantillas utilizadas en el proyecto para generar contenido dinámico.
- **txt**: Carpeta que almacena archivos de texto, probablemente recursos auxiliares o documentos de referencia.

### Uso

- Este proyecto se compone de varios archivos y utiliza Node.js para crear un servidor web y gestionar la lógica de generación de contenido dinámico. A continuación, encontrarás una descripción detallada sobre el uso de cada archivo y su función en el proyecto:

### Archivos Principales

- **index.js**: El corazón del proyecto. Crea un servidor web mediante el módulo http, maneja las solicitudes entrantes y envía respuestas adecuadas en función de la URL solicitada. Además, emplea los módulos url y slugify para gestionar las URL de manera eficiente.

### Módulos Personalizados

- **replaceTemplate.js**: Este módulo es esencial para sustituir marcadores de posición en las plantillas HTML con datos dinámicos. Facilita la generación de contenido HTML único y atractivo para la página de vista previa de productos y la página de resumen.
Carpeta templates
Aquí se albergan las plantillas HTML que generan contenido dinámico en el servidor. Estas plantillas contienen marcadores de posición que son reemplazados por datos reales mediante el módulo replaceTemplate.js.

## Carpeta dev-data

- **data.json:** Este archivo JSON contiene ejemplos de datos de productos. Estos datos son fundamentales para generar contenido dinámico en las páginas del sitio web.
Uso del Servidor
El servidor, implementado en index.js, responde a diferentes rutas URL de la siguiente manera:

- / o /overview: Muestra una vista general del contenido con tarjetas de productos generadas dinámicamente. Los datos se extraen de data.json y se integran en la plantilla template-overview.html.

- /product?id=: Muestra los detalles de un producto específico, identificado por el ID proporcionado en la consulta. Los detalles son tomados de data.json y se incrustan en la plantilla template-product.html.

- /api: Devuelve los datos contenidos en data.json en formato JSON.

- Si la URL no coincide con ninguna de las rutas mencionadas anteriormente, se devuelve una página de error 404.

### Instrucciones de Instalación

1. Clona este repositorio  local.
2. Asegúrate de tener Node.js instalado.
3. Abre una terminal y navega hasta el directorio del proyecto.
4. Ejecuta `npm install` para instalar las dependencias.

## Instalar dependencias

- Para poder navegar el servidor debes de descargar las dependencias con : 
 `npm install`

 ### Ejecutar el servidor 
 - `node index.js`
  
  ### Explorar servidor 
- http://localhost:8000/overview: Muestra una vista general del contenido.
- http://localhost:8000/product?id=0: Muestra los detalles del primer producto.
- http://localhost:8000/api: Devuelve los datos en formato JSON.

## Detener el servidor 

- Cuando hayas terminado de explorar, puedes detener el servidor presionando Ctrl + C en la terminal donde se está ejecutando.

 - **Nota**: Asegúrate de tener Node.js instalado en tu máquina antes de comenzar. Si aún no lo tienes, puedes descargarlo desde https://nodejs.org/.

 ### Código del Servidor

En este proyecto, el archivo `index.js` contiene el código principal para crear y ejecutar el servidor web. A continuación se presenta una descripción de las principales partes del código:

`javascript`
````node
const fs = require('fs');
const http = require('http');
const url = require('url');
const slugify = require('slugify');
const replaceTemplate = require('./modules/replaceTemplate.js');
````

### Explicación del codigo del servidor 

- En esta sección, se importan los módulos necesarios y se leen los datos del archivo data.json. Los módulos son:

- **fs**: Permite trabajar con el sistema de archivos, como leer archivos.
- **http**: Proporciona funcionalidades para crear un servidor HTTP.
- **url**: Ayuda a analizar y manipular URLs.
- **slugify**: Utilizado para crear indicadores de URL amigables.
- **replaceTemplate**: Un módulo personalizado que reemplaza marcadores en las plantillas HTML.

## Codeando

const server = http.createServer((req, res) => {
    const { query, pathname } = url.parse(req.url, true);

    if (pathname === '/' || pathname === '/overview') {
        /* ... Lógica para la vista general */
    } else if (pathname === '/product') {
        /* ... Lógica para la página de producto */
    } else if (pathname === '/api') {
        /* ... Lógica para la ruta de la API */
    } else {
        /* ... Lógica para manejar errores 404 */
    }
});

server.listen(8000, 'localhost', () => {
    console.log('El servidor está escuchando en el puerto 8000');
});

- utilizmos los módulos http, url, slugify y el módulo personalizado replaceTemplate para crear un servidor web. A continuación, se describe cada parte relevante del código:

`const { query, pathname } = url.parse(req.url, true);: Extrae la URL y sus componentes para manejar las rutas y parámetros de consulta.`

Manejo de Rutas:

- / o /overview: Muestra la vista general del contenido utilizando plantillas y datos dinámicos.
- /product: Muestra los detalles de un producto específico utilizando datos de data.json y una plantilla.
- replaceTemplate: Es un módulo personalizado que se utiliza para reemplazar marcadores en las plantillas HTML con datos dinámicos.

`server.listen(8000, 'localhost', () => {...}: Inicia el servidor en el puerto 8000 y muestra un mensaje en la consola cuando el servidor está listo para recibir solicitudes.`


### Contribución

Si deseas contribuir a este proyecto, sigue estos pasos:

1. Haz un fork de este repositorio.
2. Crea una rama para tu función/mejora: `git checkout -b feature/nueva-funcion`.
3. Realiza tus cambios y commitea: `git commit -m "Agregada nueva función"`.
4. Sube tus cambios a tu repositorio: `git push origin feature/nueva-funcion`.
5. Abre una Pull Request en este repositorio.

