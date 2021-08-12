---
title: CDSLab
has_children: true
nav_order: 2
---

# Componentes de CDSLab

Bienvenidos a la documentación oficial de la plataforma [CDSLab](https://github.com/fenfisdi/cdslab),
desarrollada por el grupo FEnFiSDi como una iniciativa de código abierto para brindar herramientas
de soporte para investigadores, equipos de toma de decisiones y el público en general interesado en el
modelamiento de enfermedades contagiosas.

Este proyecto busca convertirse en un entorno de trabajo que brinde diversas herramientas
en el modelamiento epidémico, usando herramientas de código abierto y cómputo de alto
rendimiento.

Como grupo y proyecto de código abierto buscamos de forma constante contribuyentes, por lo
cual extendemos una invitación a la comunidad científica que esté interesada en
contribuir a unirse a nuestros esfuerzos por producir una herramienta libre y efectiva.

## Modelos computacionales disponibles

### Modelos Basados en Agentes

El módulo [CDSLib_agents](https://github.com/fenfisdi/cdslib_agents) permite la
implementación de modelos basados en agentes para el estudio de las dinámicas de contagio
en diversos escenarios. Su diversidad y generalismo permiten simular desde espacios
pequeños(como un parque) hasta la totalidad de una ciudad.

### Dinjo y Modelos Compartimentales

#### Dinjo
El módulo [Dinjo](https://github.com/fenfisdi/dinjo) permite tener un entorno generalizado
de solución de modelos compartimentales, permitiendo implementar modelos deterministas que
describan epidemias, de forma eficiente y optimizada. Provee suficiente generalización
para ser utilizado más allá del alcance de CDSLib, ya que no es únicamente un optimizador
de ecuaciones diferenciales, sino que representa un conjunto de herramientas que pueden
ser utilizadas de forma amplia en el campo de solución de ecuaciones diferenciales. Dinjo es el
fruto del esfuerzo de uno de nuestros estudiantes e investigador, __Juan Esteban
Aristizabal__.

#### Modelos Compartimentales
Modelos compartimentales se basa en los fundamentos sólidos de Dinjo, haciendo uso de
sus generalidades para implementar un conjunto esencial de modelos de ecuaciones
diferenciales, los cuales se ofrecen al modelador con el fin de brindar un entorno rápido
y fácil de utilizar, que se configura a través de parámetros de acuerdo al tipo de modelo.
En este momento, haciendo uso de Dinjo se posee una implementación de los siguientes
modelos:
- SIR
- SIRV
- SEIRV
- Y una versión modificada de SEIRV que surge en el seno de nuestro equipo.

## Interfaz de usuario

Nuestros modelos computacionales además de poseer bases algorítmicas funcionales y que
pueden utilizadas de forma independiente y manipuladas mediante su interface en Python,
cuentan con una plataforma web, en la cual los investigadores podrán crear una cuenta y
realizar las simulaciones deseadas. A continuación se listan algunos videos con tutoriales
de uso de la plataforma:

- [Cómo crear una cuenta - Tutorial CDSLab](https://youtu.be/kCc4AFqQRRY)
- [Cómo crear un modelo SIR (ejemplo 1) - Tutorial CDSLab](https://youtu.be/ik1f8NxHqe8)

Esta plataforma web también se brinda como parte del
proyecto de código abierto y puede ser implementada de forma directa siguiendo las
instrucciones adjuntas en cada uno de sus módulos. Para realizar esta tarea de la forma
deseada, hemos dispuesto de un tipo de arquitectura de software conocida como
__Arquitectura por Microservicios__ que consiste en la creación de pequeños módulos que
funcionan de forma independiente pero hacen uso estructurado de los demás recursos para
permitir así un entorno estable, seguro y fácil de mantener a largo plazo.


 ![Arquitectura](arquitectura.png)


Nuestra interfaz se puede encontrar en el repositorio [CDSLab_webpage](https://github.com/fenfisdi/cdslab_webpage)
y está soportada por los microservicios mencionados a continuación

### CDSLab Users

El módulo [CDSLab_users_api](https://github.com/fenfisdi/cdslab_users_api) quien es el
encargado de permitir operaciones de manipulación sobre las bases de datos de usuarios, se
encarga de tareas como modificar el estado de un usuario, encontrar su localización en el
almacenamiento local y demás.

### CDSLab Auth
El módulo [CDSLab_auth](https://github.com/fenfisdi/cdslab_auth), quien es el encargado de
brindar la seguridad necesaria para la autenticación/autorización del ingreso a la
plataforma web.

### CDSLab Management

El módulo [CDSLab_management](https://github.com/fenfisdi/cdslab_management) quien es el
encargado de proveer fácilidad de configuración del entorno en que se realizan las
simulaciones. Realiza tareas desde la manipulación de las plantillas de correo que se
envían a los usuarios a modo de notificación, como el manejo automático del almacenamiento
del dispositivo.


### CDSLab ErrorLog

El módulo [CDSLab_error_log](https://github.com/fenfisdi/cdslab_error_log) quien es el
encargado de registrar de forma estructurada los errores que se presentan en la ejecución
de los intrincados procedimientos ocurridos en CDSLib, permitiendo así que se realice un
seguimiento adecuado de cualquier falla posible, y darles la solución apropiada.

### CDSLab File

El módulo [CDSLab_file_api](https://github.com/fenfisdi/cdslab_file_api) quien es el
encargado de dar estructura al almacenamiento de archivos que se requieren para las
simulaciones. De forma sincrónica, permite el intercambio de archivos entre la plataforma
y el usuario.

### CDSLab CModels

El módulo [CDSLab_cmodels_api](https://github.com/fenfisdi/cdslab_cmodels_api) quien es el
encargado de implementar la interfaz gráfica de los modelos compartimentales, hace uso
extensivo de Dinjo para permitir implementar modelos predeterminados que faciliten un
rápido y efectivo modelamiento.
 
### CDSLab Agents

Dada la gran complejidad de los modelos basados en agentes, la interfaz de usuario que se
provee para los modelos basados en agentes se encuentra compuesta por 3 módulos
principales:
- [CDSLab_agents_config](https://github.com/fenfisdi/cdslab_agents_config_api) quien es el
  encargado de permitir realizar la configuración de todos los parámetros atribuidos a los
modelos basados en agentes.
- [CDSLab_api_cloud](https://github.com/fenfisdi/cdslab_api_cloud) quien es el encargado
  de comunicar los parámetros y activar las máquinas virtuales en la nube con las
capacidades requeridas para realizar el cómputo con los parámetros solicitados.
- [CDSLab_agents_simulation](https://github.com/fenfisdi/cdslab_agents_simuliation_api)
  quien es el encargado de comunicarse de forma directa con la librería de
[CDSLib_agents](https://github.com/fenfisdi/cdslib_agents).


## Arquitectura en la nube

 ![Arquitectura API Cloud](arquitectura-APICloud.png)

Para asegurar un escalamiento de la cantidad de agentes que se pueden simular, se ha
decidido utilizar una arquitectura basada en servicios de Google Cloud. A continuación
se explica el flujo de su funcionamiento y los elementos responsables de cada paso:

1. **Api Cloud**, al Api le llega como parámetro:
  - Parámetros de Simulación.
  - Recursos de Maquinas
  - Cantidad de Maquinas
2. **Api Cloud**, identifica los archivos en **OnPremise** que deben ser enviados a **CloudStorage de Parámetros**.
3. **Api Cloud**, se crean tantas máquinas virtuales como lo indique el parámetro de ingreso y se envían el diccionario de datos, a cada una.
4. **Api Cloud**, se suben a **CloudStorage de Parametros** los archivos requeridos para simulación.
5. **ApiAgentBasedMode**, ejecuta el modelo basado en agentes con el diccionario y los archivos de parámetros leídos desde el **CloudStorage de Parámetros**.
6. **ApiAgentBasedModel**, al finalizar la simulación almacena los resultados en el **CloudStorage de Resultados**. Esta api notifica al **ApiCloud** que terminó la ejecución.
7. **ApiCloud**, al tener el reporte de finalización de todas las simulaciones, crea una máquina donde corre **ApiConsolidateAgentBasedModel**.
8. **ApiConsolidateAgentBasedModel**, lee los N resultado de la simulación, ejecuta su  lógica, y generará unos archivos de salida.
9. **ApiConsolidateAgentBasedModel**, se encarga de copiar los archivos resultados de la simulación en infraestructura **onPremise**.