# BDD con Cucumber

## ¿Qué es BDD ?
    
**Business-Driven Development (BDD)** es un enfoque de prueba derivado de la metodología Test-Driven Development (TDD).
En BDD, las pruebas se basan principalmente en el comportamiento de los sistemas. Este enfoque define varias formas
de desarrollar una característica en función de su comportamiento.
En la mayoría de los casos, el enfoque **Given-When-Then** se usa para escribir casos de prueba.
    

## Modelo de tres etapas de BDD

1. **Discovery**

    Primero se descubre, plantea el scope o alcance del comportamiento requerido por la historia de usuario.

2. **Formulation**

    Luego se formula las especificaciones en un lenguaje entendible por todas las partes.
        
3. **Automation**

    Se automatiza lo formulado para verificar el correcto funcionamiento del sistema.

## Gherkin

**Gherkin** Es un lenguaje que nos permite escirbir casos de prueba con una sintaxis que utiliza un conjunto de 
palabras clave especiales para dar estructura y significado a las especificaciones ejecutables. Cada palabra clave
se traduce a muchos idiomas hablados.
La mayoría de las líneas en un documento de Gherkin comienzan con una de las siguientes **palabras clave**.


- **Palabras clave principales:**

    * `Feature`
    * `Rule` (a partir de Gherkin 6)
    * `Example`(o Scenario)
    * `Given`, `When`, `Then`, `And`, `But` para los pasos (o *)
    * `Background`
    * `Scenario Outline` (o `Scenario Template`)
    * `Examples`
        
- **Palabras clave secundarias:**

    * `"""` (Doc Strings)
    * `|` (Tablas de datos)
    * `@` (Etiquetas)
    * `#` (Comentarios)

        - **Given:** contexto para el escenario. Ponemos al sistema en un estado específico, listo para que se desarrolle el escenario.
        - **When:** es una Acción. Algo que le sucede al sistema que hará que le suceda algo más: un resultado.
        - **Then:** es el resultado. El comportamiento que esperamos del sistema cuando esta acción ocurre en el contexto.

## Ejemplos Gherkin
~~~
    Feature: Cambiar logo y el copy del nombre del producto (Login).
        #Escenario con 3 pasos.
    Scenario: Agregar nuevo logo al Login.
        Given: Se ha cambiado el logo anterior del login, por el nuevo.
        When: ingresamos a la pantalla del Login.
        Then: visualizamos el nuevo logo.

   Feature: Hacer una busqueda en Google
       Como usuario web, queiero buscar en google para informarme sobre BDD.
   Scenario: Busqueda simple en google sobre BDD.
       Given: Un navegador web en la página de Google.
       When: Se introduce la palabra clave de busqueda **BDD** en Google.
       Then: se muestra el resultado de **BDD**
       And: Se muestran los siguientes resultado relacionados.

    |releated          |                 
    |TDD               |
    |ATDD              |
    |Gherkin           |
~~~

## Como instalar Cucumber con NodeJs y NPM

1. Primero asegurarse de tener instalado una versión actualizada de **NodeJs** y **NPM**:

    ~~~
   $ node -v
   $ npm -v 
    ~~~

2. Si surge algun error al correr los anteriores comandos, deberás reinstalar Node:

    - [Instalar Node](https://nodejs.org/en/download/)

3. Crear un directorio para nuestro proyecto:

    `$ mkdir nombreProyecto`

4. Ir al directorio:

    `$ cd nombreProyecto`

5. Primero crear el `package.json` que contendrá los paquetes de NPM que necesitamos para nuestro proyecto y agregar el paquete de **Cucumber** en el:

    ~~~
    $ npm init -y
    $ npm install -D cucumber
    ~~~

6. Opcionalmente podemos agregar `cucumber-pretty` para formatear nuestro codigo:

    `$ npm install -D cucumber-pretty`

7. Ejecutar el comando `cucumber-js -f node_modules/cucumber-pretty` para verificar que todo funcione correctamente:

    `$ ./node_modules/.bin/cucumber-js -f node_modules/cucumber-pretty`

8. Hay una forma mas amigable de correr **Cucumber**:

      - Editar `package.json`
      - Cambiar la linea `test` abajo de `script` de la opcion predeterminada a: `cucumber-js`

        ~~~
        {
            // ...
            "scripts": {
            "test": "cucumber-js -f node_modules/cucumber-pretty"
            },
            // ...
        }
        ~~~

9. Todo listo, si ejecutamos `npm test`, veremos un pass de Cucumber sin escenarios o steps para correr:

    ~~~
   $ npm test

   > nombreProyecto-js@1.0.0 test /home/usuario/cucumber/nombreProyecto-js
   > cucumber-js -f node_modules/cucumber-pretty

   0 scenarios
   0 steps
   0m00.000s
    ~~~

10. Finalmente instalaremos `hamjest` para tener mas afirmaciones positivas:
    
    `$ npm install -D hamjest`