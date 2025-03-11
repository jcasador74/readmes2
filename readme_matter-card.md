
# matter-card

MatterCard es un web component que genera una card. Forma parte del catálogo corporativo de Web Components de la Junta de Andalucía.

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
    import from '@matter/matter-card/dist/matter-card'
    ```
2. Una vez importado, llamar a dicho web-component a partir de su etiqueta propia individual. Esta llamada se debe realizar desde el fichero .html donde se quiera mostrar el web-component:
    ```html 
    <matter-card
        stylesheetVersion='latest'
        typeCard="vertical"
        imageMainCard="https://placehold.co/800x450?text=16:9"
        imageMainAltCard="Placeholder image"
        imageIconCard="https://placehold.co/40x40?text=1:1"
        imageIconAltCard="Placeholder image"
        category="Technology"
        title="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed feugiat tincidunt nisl, a maximus justo. Cras ut urna in neque maximus ultricies eget sit amet lacus.s"
        urlLink="https://example.com"
        date="2024-12-13"
        subtitle="Lorem ipsum dolor sit ame"
        description="Web Components are becoming increasingly popular for building reusable UI components."
        links='[
          {"linkUrl": "https://juntadeandalucia.es", "textContent": "Pasen"},
          {"linkUrl": "https://juntadeandalucia.es", "textContent": "Calendario escolar"},
          {"linkUrl": "https://juntadeandalucia.es", "textContent": "Acceso a la universidad y másteres"}
        ]'
        metadatas='[
            { "term": "Organismo", "description": "Turismo, Cultura y Deporte"},
            { "term": "Tipo", "description": "Estadística. Incluida en el Plan Estadístico..." }
          ]'
        social='[
          {"url": "https://facebook.com", "name": "facebook", "icon": "fab fa-facebook"},
          {"url": "https://twitter.com", "name": "twitter", "icon": "fab fab fa-x-twitter"},
          {"url": "https://linkedin.com", "name": "linkedin", "icon": "fab fa-linkedin"},
          {"url": "https://linkedin.com", "name": "linkedin", "icon": "fab fa-linkedin"},
          {"url": "https://linkedin.com", "name": "linkedin", "icon": "fab fa-linkedin"}
        ]'>    
    </matter-card>
    ```


## Estructura completa

```html
<matter-card
    stylesheetVersion='latest'
    typeCard="vertical"
    imageMainCard=""
    imageMainAltCard=""
    imageIconCard=""
    imageIconAltCard=""
    category=""
    title=""
    urlLink="
    date=""
    subtitle=""
    description=""
    links='[
      {"linkUrl": "", "textContent": ""},
      ...
    ]'
    metadatas='[
        { "term": "", "description": ""},
         ...
      ]'
    social='[
      {"url": "", "name": "", "icon": ""},
      ...
    ]'>   
</matter-card>
```

## Props

| Propiedad            | Tipo     | Descripción                                                                                                 |
| :------------------- | :------: | :-------------------------------------------------------------------------------------------------------- |
| `stylesheetVersion`  | `String` | Establece la versión de la hoja de estilos a utilizar. Por defecto es `"latest"`.                          |
| `typeCard`           | `String` | Define el tipo de la tarjeta. Puede ser `"vertical"` o `"horizontal"`.                                      |
| `imageMainCard`      | `String` | URL de la imagen principal de la tarjeta. Si no se proporciona, se dejará vacío.                           |
| `imageMainAltCard`  | `String` | Texto alternativo de la imagen principal, útil para accesibilidad y SEO.                                    |
| `imageIconCard`      | `String` | URL de la imagen del ícono de la tarjeta. Si no se proporciona, se dejará vacío.                           |
| `imageIconAltCard`  | `String` | Texto alternativo de la imagen del ícono, útil para accesibilidad y SEO.                                    |
| `title`              | `String` | Título que se mostrará en la tarjeta.                                                                       |
| `urlLink`            | `String` | URL a la que se enlaza la tarjeta. Por defecto es `"#"`, lo que indica que no tiene enlace.                 |
| `subtitle`           | `String` | Subtítulo que se mostrará debajo del título en la tarjeta.                                                  |
| `description`        | `String` | Descripción que proporciona detalles adicionales sobre el contenido de la tarjeta.                          |
| `category`           | `String` | Categoría que clasifica la tarjeta, por ejemplo, `"Tecnología"`.                                            |
| `date`               | `String` | Fecha asociada a la tarjeta, como la fecha de publicación o el evento relacionado.                          |
| `metadatas`          | `Array`  | Array de objetos con términos y descripciones, usados para proporcionar metadatos adicionales.              |
| `links`              | `Array`  | Array de objetos con enlaces. Cada objeto tiene las propiedades `linkUrl` (URL del enlace) y `textContent` (texto del enlace). |
| `social`             | `Array`  | Array de objetos con redes sociales. Cada objeto contiene `url`, `name` (nombre de la red social) e `icon` (icono de la red social). |



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
  "name": "@matter/matter-card",
  "type": "moleculas",
  "version": "1.2.0",
  "description": "A web component of MSD JdA Catalog",
  "author": "Junta de Andalucía",
  "license": "EUPL-1.2",
  "main": "src/matter-card",
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
        { from: "./demo/matter-button.stories.js", to: 'story' + '/' + PackageType + '/' + PackageName },
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
