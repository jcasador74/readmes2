# matter-calendar

Matter-calendar genera un calendario que permite visualizar el contenido de un mes,segregado por días. Su principal función es destacar por medio del atributo color y por orden cronológico aspectos relevantes. El calendario permite el acceso directo a páginas de destino, donde el usuario puede ampliar información sobre evento/actividad a desarrollar. Forma parte del catálogo corporativo de Web Components de la Junta de Andalucía.

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
5. Se accede a esta carpeta y se procede a configurar el archivo npm para acceder a los átomos y moléculas que conforman el organismo:
    ```
    npm config set @matter:registry=http://nexus.paas.junta-andalucia.es/repository/msd.npm-private/
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
    import from '@matter/matter-calendar/dist/matter-calendar'
    ```
2. Una vez importado, llamar a dicho web-component a partir de su etiqueta propia individual. Esta llamada se debe realizar desde el fichero .html donde se quiera mostrar el web-component:

  ```html
  <matter-calendar
    lang="es"
    showDays="${true}"
    showYear="${true}"
    showArrows="${true}"
    endpointUrl="https://apim-ptent-pro.paas.junta-andalucia.es/datasets/contentapi/1.0.0/boja/calendario?fechaDesde=now-365d&fechaHasta=now"
    inputDate="bojaDate"
    inputUrl="enlace"
    inputEventsByDay="boja"
    inputNodeRoot="resultado"
    inputMoreUrl="https://www.juntadeandalucia.es/eboja/2020.html"
    inputMoreTitle="Ir a boletines anteriores"
  ></matter-calendar>
  ```

## Calendario para la visualización de eventos.
Esta nueva funcionalidad permite mostrar los eventos durante todo el periodo de los mismos, es decir, desde la fecha de inicio hasta la fecha de fin. Para hacer uso de él debemos utilizar estas dos nuevas propiedades:
- inputDate2: Fecha fin del evento.
- inputUrlBuscador: Esta propiedad se utiliza para enlazar al buscador en caso de que en un mismo día haya más de un evento y además, aplica un filtro a la vista pasándole como parámetros "fecha_desde" y "fecha_hasta". Ejemplo: "/actualidad/agenda?fecha_desde=2023-10-20&fecha_hasta=2023-10-22"

Ejemplo:

  ```html
  <matter-calendar
    lang="es"
    showDays="${true}"
    showYear="${true}"
    showArrows="${true}"
    endpointUrl="https://run.mocky.io/v3/86e571a6-ba4b-4dfc-92d0-fe52b9f3a565"
    inputDate="fechaInicio"
    inputDate2="fechaFin"
    inputUrl="enlace"
    inputEventsByDay=""
    inputUrlBuscador = "/actualidad/agenda"
    inputNodeRoot=""
    inputMoreUrl="/actualidad/agenda"
    inputMoreTitle="Ver agenda"
  ></matter-calendar>
  ```

## Propiedades
Para realizar la llamada del web-components es necesario tener en cuenta las siguientes propiedades:

| Prop             | Tipo    | Descripción                                                                        |
| ---------------- | ------- | ---------------------------------------------------------------------------------- |
| date             | string  | Fecha que queremos visualizar, en formato día, mes y año.                          |
| lang             | string  | Configuración regional.                                                            |
| showDays         | boolean | Indica si se muestra la fila de los días, por defecto no se muestran.              |
| showYear         | boolean | Indica si se muestra el año, por defecto no se muestran.                           |
| showArrows       | boolean | Indica si se muestra las flechas de navegación de mes, por defecto no se muestran. |
| endpointUrl      | string  | Endpoint para obtener información sobre evento/actividad.                          |
| inputDate        | string  | Clave para obtener evento/actividad del día.                                       |
| inputDate2       | string  | (opcional) Para los eventos desde la fecha de inicio hasta fecha de fin. En caso de ser eventos de un solo dia, dejar el parámetro vacío.        |
| inputUrl         | string  | Clave para obtener enlace de evento/actividad del día.                             |
| inputEventsByDay | string  | Clave para obtener cantidad de evento/actividad del día.                           |
| inputUrlBuscador | string  | Indicar url del buscador en caso de hacer uso del campo inputDate2 para la fecha de fin.                |
| inputNodeRoot    | string  | Clave para obtener toda la información de eventos/actividades.                     |
| inputMoreUrl     | string  | Url de enlace que se encuentra en la parte inferior del calendario.                |
| inputMoreTitle   | string  | Texto de url de enlace.                                                            |
| eventLabel       | string  | Campo de los datos del endpoint correspondiente al tipo de evento                  |
| eventDate        | string  | Campo de los datos del endpoint correspondiente a la fecha del evento              |
| eventDateFormat  | string  | Formato de fecha del campo de los datos del endpoint correspondiente a la fecha del evento |
| eventDescription | string  | Campo de los datos del endpoint correspondiente a la descripción del evento        |
| etiquetas        | array   | Configuración de colores para los diferentes eventos. Los objetos que contenga el array deberán seguir el siguiente formato. El evento objetivo puede ser la palabra "empty" para reconocer una cadena vacía en el valor para el campo eventLabel, una cadena concreta o la palabra "any" para que acepte cualquier valor para el campo eventLabel que no sea vacío  |

``` JSON
    {
        "target": "Evento objetivo",
        "color": "Valor hexadecimal del color con el que se quiere resaltar el evento"
    }
```     


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
  "name": "@matter/matter-calendar",
  "type": "moleculas",
  "version": "1.2.0",
  "description": "A web component of MSD JdA Catalog",
  "author": "Junta de Andalucía",
  "license": "EUPL-1.2",
  "main": "src/matter-calendar",
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
        { from: "./demo/matter-calendar.stories.js", to: 'story' + '/' + PackageType + '/' + PackageName },
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
