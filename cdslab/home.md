---
title: CDSLab
has_children: true
nav_order: 3
---

# Componentes de CDSLab

Bienvenidos a la documentación oficial de la plataforma CDSLab, desarrollada por el grupo
FEnFiSDi como una iniciativa de código abierto para brindar herramientas de soporte para
investigadores, equipos de toma de decisiones y el público en general interesado en el
modelamiento de enfermedades contagiosas.

Este proyecto busca convertirse en un entorno de trabajo que brinde diversos entornos para
el modelamiento epidémico, usando herramientas de código abierto y cómputo de alto
rendimiento.

Como grupo y proyecto de código abierto buscamos de forma constante contribuyentes, por lo
cual extendemos una invitación a la comunidad científica que esté interesada en
contribuir a unirse a nuestros esfuerzos por producir una herramienta libre y efectiva.

## Modelos computacionales disponibles

### Modelos Basados en Agentes

El módulo [CDSLib_agents](https://github.com/fenfisdi/cdslib_agents) permite la
implementación de modelos basados en agentes para el estudio de las dinámicas de contagio
en diversos escenarios, su diversidad y generalismo permiten simular desde espacios
pequeños como un parque hasta la totalidad de una ciudad.

### Dinjo y Modelos Compartimentales

#### Dinjo
El módulo [Dinjo](https://github.com/fenfisdi/dinjo) permite tener un entorno generalizado
de solución de modelos compartimentales, permitiendo implementar modelos deterministas que
describan epidemias, de forma eficiente y optimizada. Provee suficiente generalización
para ser utilizado más allá del alcance de CDSLib, ya que no es únicamente un optimizador
de ecuaciones diferenciales, sino que representa un conjunto de herramientas que pueden
ser utilizadas de forma amplia en el campo del modelamiento epidemiológico. Dinjo es el
fruto del esfuerzo de uno de nuestros estudiantes e investigador, __Juan Esteban
Aristizabal__.

#### Modelos Compartimentales
