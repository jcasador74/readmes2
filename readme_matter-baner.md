# matter-banner

MatterLink es un web component que genera un enlace personalizable que puede incluir texto y un icono. Forma parte del catálogo corporativo de Web Components de la Junta de Andalucía.

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
    import from '@matter/matter-banner/dist/matter-banner'
    ```
2. Una vez importado, llamar a dicho web-component a partir de su etiqueta propia individual. Esta llamada se debe realizar desde el fichero .html donde se quiera mostrar el web-component:
    ```html 
    <matter-banner textContent="Enlace" linkUrl="https://www.example.com"></matter-banner>
    ```

## Ejemplo de uso
### Enlace básico

```html
<matter-banner textContent="Ir a Google" linkUrl="https://google.com"></matter-banner>
```

### Enlace con icono

```html
<matter-banner textContent="Calendario" linkUrl="#" iconClass="fa-solid fa-calendar-alt"></matter-banner>
```

### Enlace con tamaño de texto y color personalizados

```html
<matter-banner textContent="Enlace Grande" linkUrl="#" textSize="h1" textColor="gray"></matter-banner>
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
