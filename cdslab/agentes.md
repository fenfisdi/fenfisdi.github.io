---
title: Agentes
parent: CDSLab
nav_order: 3
---

# Modelos Basados en Agentes

## Introducción

Un modelo epidemiológico basado en agentes permite simular una sociedad virtual de agentes (i.e. personas) que se infectan con un virus, como el SARS-CoV-2, cuando interactúan directa (i.e. por contacto) o indirectamente (i.e. transmisión por aerosoles) con una persona infecciosa. El objetivo de este modelo es hacer análisis exploratorios de los mecanismos involucrados en la transmisión y desenlaces de la enfermedad en una población. De esta manera el modelo no usa para predecir las dinámicas de la epidemia (i.e. el número de casos incidentes en los próximos días de una epidemia). Para más información sobre los modelos basados en agentes recomendamos la lectura del capítulo 1 del documento [_Epidemiología Matemática y COVID-19_](https://drive.google.com/file/d/1wPA1rOsiBwY_1y3Lgl9fNhL09NeRVpNX/view).

Un mecanismo está compuesto por elementos (o entidades) que realizan operaciones (o actividades) organizadas para producir el fenómeno de interés <sup id="backref1">[1](#ref1)</sup> <sup id="backref2">[2](#ref2)</sup> <sup id="backref3">[3](#ref3)</sup>. Al momento de incluir un mecanismo en el modelo debemos conocer y entender sus componentes y las conexiones entre ellos. El modelo nos permite comprender cómo los elementos del mecanismo operan y cómo se afectan unas con otras, pero además cómo afectan y se ven afectadas por los elementos de otros mecanismos <sup id="backref3">[3](#ref3)</sup>.

Pensemos, por ejemplo, en los elementos que componen el mecanismo de transmisión del SARS-CoV-2. Un primer elemento son las rutas de transmisión, que para este virus principalmente son aerosoles y microgotas contaminadas con el virus que emite la persona infectada <sup id="backref4">[4](#ref4)</sup>. Un segundo elemento son las condiciones del espacio donde interactúan las personas, por ejemplo, en espacios poco ventilados la transmisión por aerosoles podría tener una mayor importancia que las demás rutas <sup id="backref5">[5](#ref5)</sup>. Un tercer elemento tiene que ver con el comportamiento de las personas, es decir, dependiendo del nivel de acatamiento de las medidas de bioseguridad, se podría dar lugar o no a un posible contagio <sup id="backref5">[5](#ref5)</sup><sup id="backref6">[6](#ref6)</sup>. Y un último elemento importante es el grado de infecciosidad de la persona contagiada, el cual depende a su vez del nivel de transmisibilidad de la variante del virus y del tiempo que ha transcurrido desde que la persona se infecta con el virus <sup id="backref6">[7](#ref7)</sup>.

Como nos pudimos dar cuenta, para incluir un mecanismo en un modelo debemos tener un conocimiento más o menos detallado del mismo. Pero además, el nivel de detalle que se requiera depende de la pregunta que el investigador desea responder con el modelo. Teniendo esto en cuenta, se diseñó un algoritmo computacional lo más general posible que permitiera configurar diferentes elementos de los mecanismos, el cual hace parte de la librería [_Contagious Disease Simulation_](https://github.com/fenfisdi/cdslab). Con este se pueden diseñar diferentes modelos epidemiológicos basados en agentes para analizar las dinámicas de la epidemia (con mecanismos similares a la epidemia del COVID-19) en una ciudad  o en un lugar determinado dentro de una ciudad.

Conceptualmente el algoritmo se divide en dos partes. La primera tiene que ver con los mecanismos asociados a la transmisión y desenlace de la enfermedad y la segunda incluye algunas estrategias farmacológicas y no-farmacológicas para mitigar o contener la epidemia. La primera parte se divide a su vez en cuatro  grupos de mecanismos. El primero son aquellos que determinan los encuentros entre las personas (i.e. densidad y movilidad), el segundo tiene que ver con los determinantes del contagio (i.e. radio de dispersión del virus, comportamiento de las personas, nivel de infecciosidad, y nivel de susceptibilidad), el tercero describe la historia natural de la enfermedad de las personas contagiadas, y el cuarto permite caracterizar cada una de las personas y construir una sociedad heterogénea (i.e. diferentes edades, vulnerabilidades, susceptibilidades).

## Referencias

<a id="ref1">1</a>: Sloan, Phillip R. 1994. “Discovering Complexity: Decomposition and Localization as Strategies in Scientific Research. William Bechtel , Robert C. Richardson.” Isis. https://doi.org/10.1086/357068.
    [↩](#backref1)

<a id="ref2">2</a>: Bechtel, William, and Adele Abrahamsen. 2005. “Explanation: A Mechanist Alternative.” Studies in History and Philosophy of Science Part C: Studies in History and Philosophy of Biological and Biomedical Sciences. https://doi.org/10.1016/j.shpsc.2005.03.010.
    [↩](#backref2)

<a id="ref3">3</a>: Bechtel, William, and Adele A. Abrahamsen. 2013. “Mechanism, Dynamic.” Encyclopedia of Systems Biology. https://doi.org/10.1007/978-1-4419-9863-7_72.
    [↩](#backref3)

<a id="ref4">4</a>: Greenhalgh, Trisha, Jose L. Jimenez, Kimberly A. Prather, Zeynep Tufekci, David Fisman, and Robert Schooley. 2021a. “Ten Scientific Reasons in Support of Airborne Transmission of SARS-CoV-2.” The Lancet 397 (10285): 1603–5.
    [↩](#backref4)

<a id="ref5">5</a>: ———. 2021b. “Ten Scientific Reasons in Support of Airborne Transmission of SARS-CoV-2.” The Lancet 397 (10285): 1603–5.
    [↩](#backref5)

<a id="ref6">6</a>: GVN. 2020. “How Long Is A SARS-CoV-2 Infected Person Contagious?” October 23, 2020. https://gvn.org/how-long-is-a-sars-cov-2-infected-person-contagious/.
    [↩](#backref6)

<a id="ref7">7</a>: ———. 2021c. “Ten Scientific Reasons in Support of Airborne Transmission of SARS-CoV-2.” The Lancet 397 (10285): 1603–5.
    [↩](#backref7)

<a id="ref1">1</a>: “Tableau Public.” n.d. Accessed December 2, 2020. https://public.tableau.com/profile/medata#!/vizhome/COVID19_Medellin/COVID19_Medellin.
    [↩](#backref1)
