# matter-video

MatterVideo es un web component que genera un componente video. Forma parte del catálogo corporativo de Web Components de la Junta de Andalucía.

## Instalación  y servidor de desarrollo

Para levantar el web components en local, se deberá seguir una serie de pasos en el orden correcto, ya que sino no se podrá iniciar correctamente. Los pasos que se deben seguir son los siguientes:

1. Eliminar el fichero .npmrc para así eliminar los repositorios y usuarios almacenados y actualizarlos con los datos necesarios correctos.
    ```
    rm C:\Users\{{USER}}\.npmrc
    ```
    
2. Acceder al [repositorio de web-components del MSD](https://gitlab.juntadeandalucia.es/pt-exp-webcomponents) y seleccionar el que se necesite.
3. Clicar en el botón "Clone" y copiar el enlace HTTPS.
4. En local, se debe posicionar en la carpeta donde se quiera descargar el web-component y abrir una consola de comandos. A continuación, ejecutar el siguiente:
    ```
    git clone {{enlace HTTPS copiado}}
    ```
    Tras la ejecución de este comando, se habrá creado la carpeta del proyecto web-component que se ha seleccionado.
5. Se accede a esta carpeta y se procede a configurar el archivo npm para acceder a los átomos que conforman la molécula:
    ```
    npm config set @matter:registry=https://nexus.paas.junta-andalucia.es/repository/msd.npm-private/
    ```
6. Se instalan las dependencias del web-component:
    ```
    npm i
    ```
7. Levantar el proyecto con el servidor de webpack:
    ```
    npm start
    ```
8. El proyecto se podrá visualizar en tiempo real en la siguiente ruta: [http://localhost:3000/](http://localhost:3000/)

## Uso
Para hacer uso de este web-component se deberá realizar dos sencillos pasos:
1. Importar el compilado del web-component en el proyecto actual:
    ```bash
    import from '@matter/matter-video/dist/matter-video'
    ```
2. Una vez importado, llamar a dicho web-component a partir de su etiqueta propia individual. Esta llamada se debe realizar desde el fichero .html donde se quiera mostrar el web-component:
    ```html 
    <matter-video 
sourceVideo="https://storagecdnvlc.codev8.net/ondemand/52001e31-c4ed-4d7b-8462-734935d179be/e397d7a1-7816-41b6-a71b-26fb1a194b2b_Fast_H1500.mp4" 
sourcePoster="https://www.juntadeandalucia.es/sites/default/files/2024-06/imagen_video_presentacion_ura_ada_900x482.jpg"
defaultTextVideo="Your browser does not support the video tag." 
ratioVideo="16x9" 
stylesheetVersion="latest"
tracks='[
{
    "label": "Español",
    "kind": "subtitles",
    "srclang": "es",
    "src": "es.vtt"
},
{
    "label": "Español",
    "kind": "description",
    "srclang": "es",
    "src": "description-es.vtt"
    
}
    
]'></matter-video>
    ```

## Ejemplo de uso
### Enlace básico

```html
<matter-video 
sourceVideo="" 
sourcePoster=""
defaultTextVideo="" 
ratioVideo="" 
stylesheetVersion=""
tracks='[
{
    "label": "",
    "kind": "",
    "srclang": "",
    "src": ""
},
{
    "label": "",
    "kind": "",
    "srclang": "",
    "src": ""
    
}
    
]'></matter-video>
```


## Props

| Prop         |  Tipo   | Descripción                                                                                               |
| :----------- | :-----: | :-------------------------------------------------------------------------------------------------------- |
| textContent  | string  | El texto que se muestra en el enlace.                                                                     |
| linkUrl      | string  | La URL a la que apunta el enlace.                                                                         |
| textColor    | string  | El color del texto (green, gray, white). Por defecto no aplica color.                                     |
| textSize     | string  | Tamaño del texto (h1, h2, etc.). Por defecto mantiene el tamaño base.                                     |
| linkTarget   | string  | El destino del enlace (_self, _blank).                                                                    |
| iconClass    | string  | Clase del icono de FontAwesome (v6). Se añade antes del texto del enlace si está definida.                |
| ariaLabel    | string  | Etiqueta ARIA para mejorar la accesibilidad del enlace.                                                   |
                                                            

<br>

## Edición

Si usas VS Code recomendamos la instalación del plugin [lit-plugin extension](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin), el cual nos ayudará a la creación de plantillas usando lit-html.

Este web component como todos los del catálogo de web components de la Junta de Andalucía están desarrollados con [JavaScript](https://www.javascript.com/) y [lit](https://lit.dev).

## Linting

ESLint se encarga de comprobar los archivos JavaScript.

Se utiliza la configuración propuesta por Airbnb, una de las mejores y más reconocidas por la comunidad [.eslintrc.json](./.eslintrc.js). Más información [aquí](https://www.npmjs.com/package/eslint-config-airbnb)

Para ejecutar eslint podemos usar este script:

```bash
npm run lint
```

## Formato

[Prettier](https://prettier.io/) se utiliza para formatear el código. Ha sido preconfigurado según el estilo del Proyecto Polymer. Puede cambiar esto en `.prettierrc.json`.

## StoryBook

Para añadir una historia al storybook es necesario realizar los siguientes cambios en el Webcomponent:

1. En el fichero ```package.json```  añadir el campo ```"type": "atomos|moleculas|organismos",``` 

2. En el fichero ```package.json``` también es necesario añadir el plugin     copy-webpack-plugin 

```
{
  "name": "@matter/matter-video",
  "type": "moleculas",
  "version": "1.2.0",
  "description": "A web component of MSD JdA Catalog",
  "author": "Junta de Andalucía",
  "license": "EUPL-1.2",
  "main": "src/matter-video",
...
...
 "devDependencies": {
    "@babel/core": "^7.14.3",
    ... 
    "copy-webpack-plugin": "^12.0.2",
    ...
  }
}
```
3. En el fichero config/webpack.prod.js añadimos la información necesaria para generar los ficheros que se cargarán en el storybook

```
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
...
const package = require('../package.json');
const PackageType = package.type;
const PackageName = package.name.replace('@matter/', '');
...

  plugins: [
    ....,
    new CopyPlugin({
      patterns: [
        { from: "README.md", to: 'story' + '/' + PackageType + '/' + PackageName },
        { from: "./demo/matter-social.stories.js", to: 'story' + '/' + PackageType + '/' + PackageName },
      ],
    }),  ],

```

4. En la carpeta demo añadimos el fichero *.stories.js que montará la historia en el storybook del webcomponent.

## Producción

### **Publicación del web-component en NEXUS PRO** (https://nexus.paas.junta-andalucia.es/)

Para publicar un web-component en el entorno de NEXUS PRO, se deberá seguir los siguientes pasos:
1. Se debe eliminar el fichero .npmrc para restablecer/eliminar los repositorios y usuarios almacenados:
    ```
    rm C:\Users\{{USER}}\.npmrc
    ```
2. Se actualiza la versión en el package.json y 
3. Se instalan las dependencias del web component:
    ```
    npm i
    ```
4. Incluir en el fichero package.json las siguientes líneas de código:
    ```
    "files": [
        "dist"
    ],
    ```
5. Ejecutar el siguiente script para generar el compilado del web-component:
    ```
    npm run build
    ```
6. Se configura el repositorio donde se va a publicar el web-component, siendo este caso NEXUS PRO:
    ```
    npm config set registry https://nexus.paas.junta-andalucia.es/repository/msd.npm-private/
    ```
    ```
    npm config set @matter:registry=https://nexus.paas.junta-andalucia.es/repository/msd.npm-private/
    ```
    
7. Se configura el usuario con el que se va a publicar en NEXUS PRO:
    ```
    npm adduser --registry=https://nexus.paas.junta-andalucia.es/repository/msd.npm-private/ --always-auth
    ```
8. Finalmente, se publica la nueva versión en el NEXUS PRO:
    ```
    npm publish
    ```
