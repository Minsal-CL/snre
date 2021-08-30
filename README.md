# IG_Receta V0.7

## Control de Cambios
Esta versión incorpora cambios relacionados con la corrección de errores generados desde la validación QA al momento de publicas

### Formato de Guía

* se corrigen errores de resolución de fuentes de las imágenes
* Se corrigió error en el despliegue del menú
* se corriegieron errores de vínculos rotos con algunas descargas
* Se corrigieron todos los perfiles, extensiones y ejemplos al formato *nombreArtefacto-CL"
* Se corrigió el **diagrama de secuencia** de *dispensación* que contenía un error en la secuencia final  

### Cambios en los Recursos

* Recurso Prescription: 
 * Se corrige error en las istrucciones de **dosaje** del recurso al definir el sistema de medicion temporal con el sistema equivalente a *UCUM*
 * Se cambió la definición de la cardinalidad del **identifier**

* Recurso de Dispensación:
 * Se corrigió error en el *slice* de **performer**, dada una mala definición del *discrimnador*. Se ajusto el discriminador al valor de la ruta *function.coding.code*, generando dos códigos forzados para cada uno de los dos slices: **#Dispensador** y **#Validador**
 * Las reglas de slicing se dejaron en estado *close*
   

### Cambios en los ejemplos
* Recurso Receta:
 * Se corrigió el elemento **status** del ejemplo a el *patrón requerido* que es *completed*

* Recurso Dispensación:
 * * En el ejemplo, se ajustaron las rutas de los *system* correpondientes a códigos **UCUM** a *http://unitsofmeasure.org*

## Guía de Implementación de Receta Electrónica Nacional del MINSAL
Esta Guía presenta los servicios que deberán estar contenidos en los desarrollos que permitan la interoperabilidad de los distintos sistemas de Prescripción y Dispensación con el Sistema Nacional de Receta Electrónica. Así mismo, describe cómo se usan los recursos FHIR para cada uno de los componentes del desarrollo. Esta guía propone todos los artefactos y perfiles necesarios para conseguir los objetivos de interoperabilidad en base al estándar HL7 FHIR R4.

### Objetivo
Con esta Guía se busca otorgar las directrices necesarias para desarrollar y asegurar la interoperabilidad de los distintos sistemas informáticos asociados a atención en salud con el sistema nacional de Receta Rlectrónica de MINSAL, basado en el estándar internacional HL7 FHIR-R4.

### Específicos
* Otorgar las herramientas necesarias para generar desarrollos informáticos en base al estándar HL7 FHIR.
* Describir los distintos perfiles de usuario del sistema y los recursos asociados a cada uno.
* Ejemplificar los distintos casos de uso asociados al sistema nacional de receta electrónica.

## Artefactos

### Perfiles
Los perfiles que se han desarrollado para esta Guía de Implementación son:

* Prescripción (MedicationRequest)
* Dispensación (MedicationDispense)
* Receta (RequestGroup)
* Organización para Receta (Organization)

### Terminologías
 Los sets de valores desarrollados corresponden a los definidos en el Core-CL (Comunas, provinicias, regiones y códigos de países)
 
### Extensiones
Se definión una extensión para determinar un medicamento en formato Producto Comercial

## Desarrollo de la Guía
La Guía ha sido desarrollada en **sushi-shothand** y llevada al formato correspondiente mediante el uso de **publisher**. Para esto se requiere pasos de instalación de algunas herramientas

### Instalación
#### Paso 1: Instalación de Node.js
Para esto debe descargar https://nodejs.org/ para la versión LTS. Se debe ejecutar el instalable para que este despliegue las configuraciones básicas.

Para asegurar que quedo bien instalado ejecute desde *línea de comando* lo siguiente, lo que devolverá como resultado el núnero de versión

~~~
$ node --version
$ npm --version
~~~

#### Paso 2: Instalar Sushi
Desde *línea de comando*

~~~
$ npm install -g fsh-sushi
~~~

Verificar la instalación ejecutando

~~~
$ sushi -h
~~~
#### Pasos Adicionales
La instalación de **Node.js** y **sushi** puede implicar la instalación de herramientas para el uso posterior de **publisher**. En particular se puede requerir la instalación de  **GEM-Ruby** https://rubygems.org/pages/download, para de esta forma poder dejar habilitado **Jekyll** https://jekyllrb.com/docs/installation/

También en algunos casos se puede tener problemas en la ejecución de **publisher** vía comando java debido a permisos, por lo que se deben configurar las *variables de ambiente* de **JAVA_HOME** and **PATH**.

### Ejecutando Sushi
Para ejecutar sushi y complilar la GI se debe ejecutar desde el directorio raíz del proyecto

~~~
$ sushi .
~~~

### Ejecutando Publisher
Para publicar la GI en el template por defecto o en que se configure, desde el directorio raiz del proyecto se debe ejecutar:

~~~
$ _genonce
~~~

SUSHI utiliza el contenido de un **package.json** y un directorio **ig-data** creados por el usuario para generar las entradas del **IG Publisher**. Para un IG básico sin personalización, simplemente cree una carpeta **ig-data** vacía. Para un IG personalizado, cree y rellene la carpeta **ig-data** con contenido y configuraciones personalizadas.

### Más Información
Para mas información puede navegar por las páginas:

* http://hl7.org/fhir/uv/shorthand/2020May/sushi.html
* http://hl7.org/fhir/uv/shorthand/2020May/tutorial.html
