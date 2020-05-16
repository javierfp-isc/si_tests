# Repositorio si_tests

## Objetivo

Este repositorio contiene herramientas para la realización de tests en las tareas del módulo de SI de los ciclos de DAM y DAW

## Estructura del repositorio

**Este repositorio dispondrá de una rama (branch) para cada tarea a validar,** el nombre de la rama será un identificador ilustrativo de la tarea. Por ejemplo: la branch **sa_crear** del repositorio será la asociada a la tarea identificada como sa_crear, etc.

Por tanto deberemos descargar la branch adecuada. **Por ejemplo para ejecutar los tests de la tarea sa_crear:**

`git clone -b sa_crear git@github.com:javierfp-isc/si_tests.git`

El mismo procedimiento se aplicaría a las demás tareas descargando la rama adecuada.

## Contenidos

### Directorio de tests

En el directorio **tests** del repositorio nos encontramos la infraestructura para la realización de tests. Utilizaremos **ansible** para tal fin.

### Realización de los test

Los tests son un conjunto de pruebas que se lanzarán de forma automática en el escenario y que comprobarán si has realizado correctamente los pasos y ejercicios indicados en la práctica.

### Variables para la ejecución

Dentro del archivo **test.yaml**  hay una lista de variables que deberéis especificar para cada práctica. El tipo y número dependerá de la misma, pero como mínimo deberéis indicar vuestro **nombre** y **el token de acceso** a gitlab de vuestro usuario.

`#Variables que debe especificar el alumno`

`NOMBREALUMNO: Javier Fernández Peón`

`GITLABTOKEN: 9HMCTHQDCJAfeqsPjtzY`

*NOTAD que al ser formato YAML la sintaxis es del tipo clave: valor*

### Ejecución de los tests

Una vez instalado el módulo anterir para lanzar los test nos situamos dentro del directorio **tests** del repositorio y lanzamos desde la terminal el comando:

`ansible-playbook test.yaml`

Veremos en la salida del comando los mensajes de error si alguno de los test falla.

Si todo los tests se pasan con éxito al final del comando veremos un mensaje del tipo

**"ENHORABUENA!. Has superado todos los test"**

En caso contrario, si alguno falla el mensaje será:

**"LO SIENTO!. No has superado todos los test"**

por tanto deberás de revisar cual ha fallado y realizar las correcciones oportunas

### Archivos de log

Puedes ver también el resultado de la ejecución de los test, además de en la salida de la terminal, en los archivos

**log/test.log**: Toda la salida

**log/report.log**: Salida resumida y formateada para una lectura sencilla (en formato markdown)

## Entrega

Una vez que finalices correctamente la práctica, es decir con todos los test superados, para realizar la entrega de los resultados de ejecución de la misma deberás ejecutar el comando:

`ansible-playbook test.yaml -e entregar=yes`

Si hay algún error en los tests lo verás como se explica en el apartado anterior, **en cuyo caso la entrega no se realizará**

### Entrega forzada

Si quieres realizar la entrega **aún cuando algún test haya fallado** ejecuta el comando:

`ansible-playbook test.yaml -e entregar=yes -e force=yes`

