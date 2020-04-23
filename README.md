## BDD con Cucumber

-

## Como instalar Cucumber con NodeJs y NPM

1. Primero asegurarse de tener instalado una versión actualizada de NodeJs y NPM:

    ~~~
   $ node -v
   $ npm -v 
    ~~~

2. Si surge algun error al correr los anteriores comandos, deberás reinstalar Node.

    - [Instalar Node]{https://nodejs.org/en/download/}

3. Crear un directorio para nuestro proyecto:

    `$ mkdir Benko`

4. Ir al directorio:

    `$ cd Benko`

5. Primero crear el `package.json` que contendrá los paquetes de NPM que necesitamos para nuestro proyecto y agregar el paquete de Cucumber en el:

    ~~~
  $ npm init -y
  $ npm install -D cucumber
    ~~~

6. Opcionalmente podemos agregar `cucumber-pretty` para formatear nuestro codigo:

    `$ npm install -D cucumber-pretty`

7. Ejecutar el comando `cucumber-js -f node_modules/cucumber-pretty` para verificar que todo funcione correctamente:

    `$ ./node_modules/.bin/cucumber-js -f node_modules/cucumber-pretty`

8. Hay una forma mas amigable de correr Cucumber:

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

   > shouty-js@1.0.0 test /home/fedex/cucumber/shouty-js
   > cucumber-js -f node_modules/cucumber-pretty

   0 scenarios
   0 steps
   0m00.000s
    ~~~

10. Finalmente instalaremos `hamjest` para tener mas afirmaciones positivas:
    
    - `$ npm install -D hamjest`