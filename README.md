# Aplicación Distribuida Segura en Todos sus Frentes
## Descripción
En la **Aplicación Distribuida Segura en Todos sus Frentes** se desarrolló una aplicación capaz de permitir un acceso seguro desde el browser a la aplicación. Es decir que este garantiza autenticación, autorización e integridad de usuarios, en los que se ha creado una interfaz de inicio de sesión que permite acceso seguro desde el navegador, y donde el usuario puede iniciar sesión de forma segura en el navegador. También se implementó la funcionalidad en la que al menos dos computadores se comunican entre ellos y el acceso de servicios remotos garantiza: autenticación, autorización e integridad entre los servicios, en los que nadie puede invocar los servicios si no está autorizado. La aplicación fue desarrollada con dos códigos fuente, el primero llamado ```LoginSeguro``` y el segundo llamado ```ServicioSeguro```. En ```LoginSeguro``` el usuario puede iniciar sesión de forma segura, y este tiene su propio certificado HTTPS. ```ServicioSeguro``` se encarga de retornar una página también con su propio certificado HTTPS y su propia interfaz de usuario por aparte.

## Prerrequisitos
Para la realización y ejecución tanto del programa como de las pruebas de este, se requieren ser instalados los siguientes programas:
* [Maven](https://maven.apache.org/). Herramienta que se encarga de estandarizar la estructura física de los proyectos de software, maneja dependencias (librerías) automáticamente desde repositorios y administra el flujo de vida de construcción de un software.
* [GIT](https://git-scm.com/). Sistema de control de versiones que almacena cambios sobre un archivo o un conjunto de archivos, permite recuperar versiones previas de esos archivos y permite otras cosas como el manejo de ramas (branches).
* [Docker](https://www.docker.com/). Programa encargado de crear contenedores ligeros y portables para las aplicaciones software que puedan ejecutarse en cualquier máquina con Docker instalado, independientemente del sistema operativo que la máquina tenga por debajo, facilitando así también los despliegues.
Para asegurar que el usuario cumple con todos los prerrequisitos para poder ejecutar el programa, es necesario disponer de un Shell o Símbolo del Sistema para ejecutar los siguientes comandos para comprobar que todos los programas están instalados correctamente, para así compilar y ejecutar tanto las pruebas como el programa correctamente.

Para asegurar que el usuario cumple con todos los prerrequisitos para poder ejecutar el programa, es necesario disponer de un Shell o Símbolo del Sistema para ejecutar los siguientes comandos para comprobar que todos los programas están instalados correctamente, para así compilar y ejecutar tanto las pruebas como el programa correctamente.

```
mvn -version
git --version
java -version
docker version
```

## Instalación
Para descargar el proyecto de GitHub, primero debemos clonar este repositorio, ejecutando la siguiente línea de comando en GIT.

```
git clone https://github.com/Skullzo/AREP-Lab4.git
```

## Ejecución
Para compilar el proyecto utilizando la herramienta Maven, nos dirigimos al directorio donde se encuentra alojado el proyecto, y dentro de este ejecutamos en un Shell o Símbolo del Sistema el siguiente comando:

```
mvn package
```
## Pruebas
Para realizar las pruebas correspondientes del proyecto utilizando la herramienta Maven, nos dirigimos al directorio donde se encuentra alojado el proyecto, y dentro de este ejecutamos en un Shell o Símbolo del Sistema el siguiente comando:

```
mvn test
```

Pruebas compiladas correctamente para el código fuente **LoginSeguro**.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/Prueba1.PNG)

Pruebas compiladas correctamente para el código fuente **ServicioSeguro**.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/Prueba2.PNG)

----------

### Docker

Para verificar que en la aplicación Docker se hayan desplegado con éxito los contenedores LoginSeguro y ServicioSeguro en sus respectivos puertos, se abre la aplicación de Docker de escritorio y se hace la verificación que todos los contenedores estén corriendo en sus respectivos puertos. Como se ve en la siguiente imagen, todos los contenedores están corriendo satisfactoriamente.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/Docker1.PNG)

Para comprobar que la página web ha sido desplegada con éxito de manera local utilizando Docker, se ingresa en el navegador la siguiente URL: https://localhost:8000/. Como se puede observar, el contenedor ha sido desplegado satisfactoriamente de manera local utilizando Docker. Para poder acceder a ella, se requiere presionar primero clic en **Advanced** y luego en **Continue to localhost (unsafe)**, como se observa a continuación.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/Docker2.png)

Luego de realizar clic en **Continue to localhost (unsafe)**, se observa que la página ha sido desplegada satisfactoriamente de manera local utilizando Docker.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/Docker3.PNG)

Luego de ingresar las credenciales y presionar clic en el botón **Iniciar Sesión**, se observa claramente que la página web redirige al recurso https://localhost:8000/authorized.html, lo cual indica que el inicio de sesión ha sido exitoso y seguro, ya que este segundo recurso se maneja también usando el protocolo HTTPS, indicando que la aplicación garantiza autenticación, autorización e integridad de usuarios.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/Docker4.PNG)

----------

### AWS
Para realizar las pruebas correspondientes de la ejecución del programa en AWS, y que el contenedor se encuentra activo desde la máquina virtual, ingresamos en el navegador la siguiente URL: https://ec2-3-95-67-168.compute-1.amazonaws.com:8000. Como se puede observar, el contenedor ha sido desplegado satisfactoriamente desde la máquina virtual montada en AWS. Para poder acceder a ella, se requiere presionar primero clic en **Advanced** y luego en **Continue to ec2-3-95-67-168.compute-1.amazonaws.com (unsafe)**, como se observa a continuación.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/AWS1.png)

Luego de realizar clic en **Continue to ec2-3-95-67-168.compute-1.amazonaws.com (unsafe)**, se observa que la página ha sido desplegada satisfactoriamente en la máquina virtual.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/AWS2.PNG)

Luego de ingresar las credenciales y presionar clic en el botón **Iniciar Sesión**, se observa claramente que la página web redirige al recurso https://ec2-3-95-67-168.compute-1.amazonaws.com:8000/authorized.html, lo cual indica que el inicio de sesión ha sido exitoso y seguro, ya que este segundo recurso se maneja también usando el protocolo HTTPS, indicando que la aplicación garantiza autenticación, autorización e integridad de usuarios.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/AWS3.PNG)

## Certificados
Para poder establecer una conexión segura (HTTPS) con la aplicación, garantizando autenticación, autorización e integridad de usuarios, se realiza el respectivo procedimiento de establecimiendo de certificados con llaves para cada uno de los siguientes programas. Para esto, se realizaron dos certificados, uno por cada código fuente, que son ```LoginSeguro``` y ```ServicioSeguro```.

### Certificados en LoginSeguro
Para establecer la llave en ```LoginSeguro```, primero se ejecutó el siguiente comando dentro de la carpeta ```keystores```, carpeta que almacena todos los certificados y llaves de ```LogService```.

```
keytool -genkeypair -alias ecikeypair -keyalg RSA -keysize 2048 -storetype PKCS12 -keystore ecikeystore.p12 -validity 3650
```

Luego de ejecutar el comando, se ingresaron los datos correspondientes a cada una de las preguntas para poder crear la llave. Luego de crear la llave, el resultado se obtiene tal y como se observa en la siguiente imagen.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/LlaveLoginSeguro.PNG)

Para establecer el certificado de la llave ya creada, dentro de la misma carpeta de ```keystores``` se ejecuta el siguiente comando.

```
keytool -export -keystore ./ecikeystore.p12 -alias ecikeypair -file ecicert.cer
```

Luego de ejecutar el comando, se observa que el certificado ha sido creado satisfactoriamente para la llave en cuestión.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/CertificadoLoginSeguro.PNG)

Para crear el ```myTrustStore``` para la llave ya creada con su respectivo certificado, se ingresa el siguiente comando.

```
keytool -import -file ./ecicert.cer -alias firstCA -keystore myTrustStore
```

Luego de haber ingresado el comando, se verifica que se esté creando el ```myTrustStore``` para la llave que ha sido creada con su respectivo certificado. Luego de verificar que todos los datos retornados estén correctos, se ingresa ```yes``` para poder crear el ```myTrustStore```. Como se ve a continuación, el ```myTrustStore``` ha sido creado satisfactoriamente con su respectivo certificado.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/myTrustStoreLoginSeguro.PNG)

----------

### Certificados en ServicioSeguro
Para establecer la llave en ```ServicioSeguro```, primero se ejecutó el siguiente comando dentro de la carpeta ```keystores```, carpeta que almacena todos los certificados y llaves de ```ServicioSeguro```.

```
keytool -genkeypair -alias ecikeypair -keyalg RSA -keysize 2048 -storetype PKCS12 -keystore ecikeystore.p12 -validity 3650
```

Luego de ejecutar el comando, se ingresaron los datos correspondientes a cada una de las preguntas para poder crear la llave. Luego de crear la llave, el resultado se obtiene tal y como se observa en la siguiente imagen.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/LlaveServicioSeguro.PNG)

Para establecer el certificado de la llave ya creada, dentro de la misma carpeta de ```keystores``` se ejecuta el siguiente comando.

```
keytool -export -keystore ./ecikeystore.p12 -alias ecikeypair -file ecicert.cer
```

Luego de ejecutar el comando, se observa que el certificado ha sido creado satisfactoriamente para la llave en cuestión.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/CertificadoServicioSeguro.PNG)

Para crear el ```myTrustStore``` para la llave ya creada con su respectivo certificado, se ingresa el siguiente comando.

```
keytool -import -file ./ecicert.cer -alias firstCA -keystore myTrustStore
```

Luego de haber ingresado el comando, se verifica que se esté creando el ```myTrustStore``` para la llave que ha sido creada con su respectivo certificado. Luego de verificar que todos los datos retornados estén correctos, se ingresa ```yes``` para poder crear el ```myTrustStore```. Como se ve a continuación, el ```myTrustStore``` ha sido creado satisfactoriamente con su respectivo certificado.

![img](https://github.com/Skullzo/AREP-Lab6/blob/main/img/myTrustStoreServicioSeguro.PNG)

## Construido con
* [Maven](https://maven.apache.org/). Herramienta que se encarga de estandarizar la estructura física de los proyectos de software, maneja dependencias (librerías) automáticamente desde repositorios y administra el flujo de vida de construcción de un software.
* [GIT](https://git-scm.com/). Sistema de control de versiones que almacena cambios sobre un archivo o un conjunto de archivos, permite recuperar versiones previas de esos archivos y permite otras cosas como el manejo de ramas (branches).
* [JUnit](https://junit.org/junit5/). Framework de Java que permite la realización de la ejecución de clases de manera controlada, para poder comprobar que los métodos realizan su cometido de forma correcta.
* [NetBeans](https://netbeans.apache.org/). Entorno de desarrollo integrado libre, orientado principalmente al desarrollo de aplicaciones Java. La plataforma NetBeans permite el desarrollo de aplicaciones estructuradas mediante un conjunto de componentes denominados “módulos”. Cada uno de estos módulos sería un archivo Java conteniendo un conjunto de clases que interactarán con las APIs de NetBeans. El objetivo de esta arquitectura es favorecer el desarrollo de funcionalidades de forma independiente y la reutilización de componentes.
* [Java](https://www.oracle.com/java/). Lenguaje de programación de propósito general, es decir, que sirve para muchas cosas, para web, servidores, aplicaciones móviles, entre otros. Java también es un lenguaje orientado a objetos, y con un fuerte tipado de variables.
* [Docker](https://www.docker.com/). Programa encargado de crear contenedores ligeros y portables para las aplicaciones software que puedan ejecutarse en cualquier máquina con Docker instalado, independientemente del sistema operativo que la máquina tenga por debajo, facilitando así también los despliegues.
* [AWS](https://aws.amazon.com/es/). Conjunto de herramientas y servicios de cloud computing de Amazon, que engloba una gran cantidad de servicios para poder realizar distintos tipos de actividades en la nube. Desde almacenamiento a la gestión de instancias, imágenes virtuales, desarrollo de aplicaciones móviles, etc.
* [CircleCI](https://circleci.com/). Plataforma moderna de integración continua y entrega continua (CI / CD) que se encarga de automatizar la construcción, pruebas e implementación de software.

     [![CircleCI](https://circleci.com/gh/circleci/circleci-docs.svg?style=svg)](https://app.circleci.com/pipelines/github/Skullzo/AREP-Lab6)

## Autor
[Alejandro Toro Daza](https://github.com/Skullzo)
## Licencia & Derechos de Autor
**©** Alejandro Toro Daza, Estudiante de Ingeniería de Sistemas de la [Escuela Colombiana de Ingeniería Julio Garavito](https://www.escuelaing.edu.co/es/).

Licencia bajo la [GNU General Public License](https://github.com/Skullzo/AREP-Lab6/blob/main/LICENSE).
