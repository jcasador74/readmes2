
# matter-list-links

MatterCard es un web component que genera un listado de enlaces. Forma parte del catálogo corporativo de Web Components de la Junta de Andalucía.

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
    import from '@matter/matter-list-links/dist/matter-list-links'
    ```
2. Una vez importado, llamar a dicho web-component a partir de su etiqueta propia individual. Esta llamada se debe realizar desde el fichero .html donde se quiera mostrar el web-component:
    ```html 
    <matter-list-links typeList="principal" headerText="Te interesa" stylesheetVersion="latest" descriptionList="Nullam id est non mauris vestibulum mattis. Duis et lectus scelerisque, consectetur nulla et, aliquam quam. Integer porttitor malesuada mi" lists='[
    {
        "items": [
            {   
                
                "link": {
                    "textContent": "Ofertas de empleo - Junta de Andalucía",
                    "linkUrl": "https://www.juntadeandalucia.es/organismos/sae/areas/ofertas-empleo/ofertas-empleo.html",
                    "textColor": "",
                    "textSize": "h5",
                    "iconClass": "fa-solid fa-star",
                    "textWeight": ""
                },
                "descriptionLink": "Nullam id est non mauris vestibulum mattis. Duis et lectus scelerisque, consectetur nulla et, aliquam quam. Integer porttitor malesuada mi, at eleifend elit auctor quis. Quisque pellentesque sapien ut nunc congue cursus. Praesent dictum dui nec odio congue facilisis. Donec id pretium odio. Vestibulum aliquam tempus quam nec vehicula. Quisque vel dui sit amet ex mattis molestie non id lorem. Ut ultricies metus orci, id facilisis purus pretium ut."

                
            },
            {

                "link": {
                    "textContent": "Ofertas de empleo - Junta de Andalucía",
                    "linkUrl": "https://www.juntadeandalucia.es/organismos/sae/areas/ofertas-empleo/ofertas-empleo.html",
                    "textColor": "",
                    "textSize": "h5",
                    "iconClass": "fa-solid fa-star",
                    "textWeight": ""
                },
                "descriptionLink": "Nullam id est non mauris vestibulum mattis. Duis et lectus scelerisque, consectetur nulla et, aliquam quam. Integer porttitor malesuada mi, at eleifend elit auctor quis. Quisque pellentesque sapien ut nunc congue cursus. Praesent dictum dui nec odio congue facilisis. Donec id pretium odio. Vestibulum aliquam tempus quam nec vehicula. Quisque vel dui sit amet ex mattis molestie non id lorem. Ut ultricies metus orci, id facilisis purus pretium ut."

            }
        ]
    }
]'
moreOptionUrl="http://"
moreOptionTitle="Más detalles de enlace"></matter-list-links>```


## Estructura completa

```html
<matter-list-links typeList="" headerText="" stylesheetVersion="" descriptionList="i" lists='[
    {
        "items": [
            {   
                
                "link": {
                    "textContent": "",
                    "linkUrl": "",
                    "textColor": "",
                    "textSize": "",
                    "iconClass": "",
                    "textWeight": ""
                },
                "descriptionLink": ""

                
            },
        ...
        ]
    }
]'
moreOptionUrl=""
moreOptionTitle=""></matter-list-links>
```

## Props

| Propiedad         | Tipo     | Descripción                                                                 |
|------------------|---------|-----------------------------------------------------------------------------|
| `stylesheetVersion` | String  | Versión de las hojas de estilo a utilizar.                               |
| `typeList`       | String  | Tipo de lista (`secundario` o `principal`).                                |
| `headerText`     | String  | Encabezado de la lista.                                                    |
| `descriptionList` | String  | Descripción de la lista.                                                   |
| `lists`          | Array   | Array con los datos de cada lista.                                         |
| `moreOptionUrl`  | String  | URL para la opción de "Más opciones".                                      |
| `moreOptionTitle`| String  | Título para la opción de "Más opciones".                                  |



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
  "name": "@matter/matter-list-links",
  "type": "moleculas",
  "version": "1.2.0",
  "description": "A web component of MSD JdA Catalog",
  "author": "Junta de Andalucía",
  "license": "EUPL-1.2",
  "main": "src/matter-list-links",
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
        { from: "./demo/matter-list-links.stories.js", to: 'story' + '/' + PackageType + '/' + PackageName },
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
