---
title: CDSLab
has_children: true
nav_order: 2
---

# Componentes de CDSLab

Bienvenidos a la documentación oficial de la plataforma CDSLab, desarrollada por el grupo
FEnFiSDi como una iniciativa de código abierto para brindar herramientas de soporte para
investigadores, equipos de toma de decisiones y el público en general interesado en el
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
realizar las simulaciones deseadas. Esta plataforma web también se brinda como parte del
proyecto de código abierto y puede ser implementada de forma directa siguiendo las
instrucciones adjuntas en cada uno de sus módulos. Para realizar esta tarea de la forma
deseada, hemos dispuesto de un tipo de arquitectura de software conocida como
__Arquitectura por Microservicios__ que consiste en la creación de pequeños módulos que
funcionan de forma independiente pero hacen uso estructurado de los demás recursos para
permitir así un entorno estable, seguro y fácil de mantener a largo plazo.

Nuestra interfaz está compuesta por los microservicios mencionados a continuación

### CDSLab_auth
El módulo [CDSLab_auth](https://github.com/fenfisdi/cdslab_auth), quien es el encargado de
brindar la seguridad necesaria para la autenticación/autorización del ingreso a la
plataforma web.

### CDSLab_management

El módulo [CDSLab_management](https://github.com/fenfisdi/cdslab_management) quien es el
encargado de proveer fácilidad de configuración del entorno en que se realizan las
simulaciones. Realiza tareas desde la manipulación de las plantillas de correo que se
envían a los usuarios a modo de notificación, como el manejo automático del almacenamiento
del dispositivo.

### CDSLab_users_api

El módulo [CDSLab_users_api](https://github.com/fenfisdi/cdslab_users_api) quien es el
encargado de permitir operaciones de manipulación sobre las bases de datos de usuarios, se
encarga de tareas como modificar el estado de un usuario, encontrar su localización en el
almacenamiento local y demás.

### CDSLab_cmodels_api

El módulo [CDSLab_cmodels_api](https://github.com/fenfisdi/cdslab_cmodels_api) quien es el
encargado de implementar la interfaz gráfica de los modelos compartimentales, hace uso
extensivo de Dinjo para permitir implementar modelos predeterminados que faciliten un
rápido y efectivo modelamiento.
