---
title: Fundamentos de modelación epidemiológica
parent: CDSLab
nav_order: 1
---

# Fundamentos de modelación epidemiológica

## Introducción

Los modelos son herramientas esenciales en el quehacer de todas las disciplinas científicas, 
consisten en representaciones de fenómenos, situaciones o partes de ellos y sus utilidades 
varían de acuerdo a la finalidad con la que se diseñan. Es así cómo pueden servir para describir
un fenómeno, emplearse como herramientas explicativas o como vehículos de aprendizaje, usarse
como experimentos científicos, permitir predecir o controlar una realidad y hacer las veces
de herramienta de exploración epistémica al permitir descubrir nuevos objetos de estudio
<sup id="backref1">[1](#ref1)</sup> <sup id="backref2">[2](#ref2)</sup>.

Los modelos computacionales en particular posibilitan plantear, evaluar y conjeturar
respuestas a diferentes escenarios que no pueden ser explorados a través de las observaciones
al mundo real; esto se deriva de los marcos flexibles sobre los que se simula una realidad
virtual dado que la construcción conceptual sobre las que se cimientan no es fija.

## Los modelos en la epidemiología

Los modelos epidemiológicos han llevado a la comprensión de las propiedades de enfermedades
infecciosas, que en consecuencia, han sido esenciales para la toma de decisiones políticas.
Usualmente son dos las propiedades que buscan describir los modelos epidemiológicos: por
un lado buscan representar cómo progresa la enfermedad en cada individuo (historia natural)
y por otro lado, buscan describir cómo se disemina la enfermedad en la población
(dinámicas de contagio).

Hoy en día existen varias aproximaciones computacionales para describir procesos epidémicos.
En primer lugar están __los modelos compartimentales__ y sus sofisticaciones, los cuales están
basados en ecuaciones diferenciales ordinarias y cuentan con más de cien años de historia.
Pero además, existen otras aproximaciones metodológicas como lo son __los modelos estocásticos__,
__los modelos basados en datos__ y __los modelos basados en agentes__.

## Historia

Los modelos matemáticos en epidemiología nacen con __los modelos compartimentales__.
Durante las primeras décadas del siglo XX, no solo ocurrió una catastrófica pandemia de influenza
acompañada de recurrentes brotes de otras enfermedades infecciosas alrededor del mundo --como el cólera,
tifo o peste--; sino también durante estos años fue que se desarrollaron los primeros modelos matemáticos
epidemiológicos. La formulación de estos modelos fue posible luego de que fueran establecidos algunos
patrones básicos a los brotes epidémicos como la relación entre la propagación de la epidemia con el número
de personas susceptibles y de personas infecciosas <sup id="backref3">[3](#ref3)</sup> <sup id="backref4">[4](#ref4)</sup>.

El trabajo de Ross en malaria (1911) <sup id="backref5">[5](#ref5)</sup> fue un trabajo pionero al
matematizar por medio de un conjunto de ecuaciones la dinámica de la relación entre el número de infectados
y el número de mosquitos en el ambiente, principio que si bien hoy resulta casi que intuitivo, en la época
era imposible de establecer a simple vista. Posteriormente, la colaboración entre Ross y la matemática
Hilda Hudson (1916) permitió comprender los patrones para diseñar diferentes modelos. Gracias a estos desarrollos,
se formaliza la epidemiología matemática con el trabajo de MacKendrick y Kermack (1927) <sup id="backref6">[6](#ref6)</sup>,
quienes consolidaron este concepto, proponiendo un modelo que relaciona la propagación con el número de personas
susceptibles e infectadas. Para lograrlo, separaron a la población en compartimientos o grupos según el estado
infeccioso de los individuos, es decir, en los grupos susceptibles, infectados y recuperados; el tránsito
entre los compartimientos se formuló a través de ecuaciones diferenciales ordinarias. 

Para algunos investigadores, los fundamentos de las intervenciones en salud pública nacen con
__los modelos compartimentales__ debido a que permiten resolver preguntas sobre el número de infectados
y el tiempo que puede durar un brote epidémico <sup id="backref7">[7](#ref7)</sup>.

## Características generales de los modelos epidemiológicos

Los modelos epidemiológicos buscan representar cómo se infectan los individuos de una población y cómo
progresa la enfermedad infecciosa en cada uno de ellos. A pesar de la diversidad de modelos epidemiológicos
actuales, todos los modelos describen el fenómeno como cambios de estados individuales o poblacionales, que
en modelación se conocen como variables de estado. Estos estados representan momentos clínicos o infecciosos
que experimentan los individuos, como por ejemplo ser susceptible, luego ser infeccioso y posteriormente 
recuperarse o morir (ver [Figura 1](#fig1) costado izquierda). El tránsito y en general la relación entre
las variables de estado depende de elementos del modelo llamados parámetros que condicionan el cambio
entre, por ejemplo, el estado infectado al recuperado (ver [Figura 1](#fig1) costado derecha).

{% include image.html img="Figura1.png" id="fig1" title="Figura 1" caption="Representación de los elementos de un modelo epidemiológico para describir la progresión de la enfermedad en los individuos en un caso en el cual, una vez los individuos sanos se infectan, pueden recuperarse o morir. A mano izquierda están destacadas en negrilla las variables de estado, que para este ejemplo serían las variables de estado Susceptibles, Infectados y Recuperado. A mano derecha están descritos los parámetros específicos para este modelo que serían la taas de infección, la tasa de recuperación, la tasas de pérdida de inmunidad y la tasa de mortalidad." %}

Diferentes tipos de modelos epidemiológicos abordan el sistema a diferentes escalas de resolución como es
común entre los modelos usados para representar dinámicas poblacionales. Este tipo de resolución es específica al nivel de separación o unión que hace el modelador sobre los elementos constituyentes del sistema y recibe el nombre de granularidad. Es así como un fenómeno epidemiológico puede ser representado por modelos que describen la dinámica de la población en términos de: el resultado del comportamiento de cada uno de sus individuos (microescala) o modelos de granularidad alta; la interacción de ensambles de individuos (mesoescala) o modelos de granularidad media; o el flujo entre grandes subgrupos poblacionales (macroescala) o granularidad baja. (Ver Figura 1) 




Figura 1. Representación de la granularidad, resolución o nivel de detalle con el que los modelos computacionales pueden abordar un fenómeno poblacional como una epidemia. A una escala baja de granularidad, o microescala, se busca representar al individuo, el comportamiento poblacional surge como una combinación de los comportamientos individuales. A una escala de granularidad intermedia, o mesoescala, se representan ensambles o agrupaciones de individuos y el comportamiento de la agrupación suele representarse como el comportamiento promedio de los individuos representados en la agrupación. A un nivel de detalle menor, o macroescala, el fenómeno es descrito como cambios o flujos entre subpoblaciones o compartimientos poblacionales.

Cada grado de detalle suele ser simulado a través de diferentes paradigmas metodológicos (ver Figura 2). Ya que las aproximaciones de baja resolución describen el fenómeno en términos de dinámicas poblacionales, los sistemas de ecuaciones diferenciales resultan ser bastante prácticos para describir el fenómeno epidémico, si se quiere abordar el sistema desde una perspectiva determinista. No obstante, pueden usarse métodos como las cadenas de Markov cuando se representa el sistema a través de una perspectiva probabilista. Las aproximaciones de alto grado de detalle por su parte, describen al sistema en términos de individuos que interactúan y conforman poblaciones, estos son los llamados modelos basados en agentes (MBA) y son más demandantes en términos computacionales y no suelen ser efectivos para dar respuestas numéricas (3). Existen modelos capaces de incorporar dinámicas a varias escalas, denominados modelos multiescala. 

Figura 2. Relación generalizada entre la granularidad del sistema, la aproximación computacional usual para describir sus cambios y su complejidad del sistema. Es usual que los fenómenos descritos a una resolución baja aborden el sistema con ecuaciones de cambio como pueden ser las ecuaciones diferenciales en donde las transiciones infecciosas o clínicas de los individuos se describen a través de flujos o tasas de cambio. Los modelos que abordan con una alta resolución el fenómeno, suelen considerar probabilidades de cambio para describir las transiciones infecciosas o clínicas de los individuos, debida a que aumentar la granularidad del modelo involucra ampliar la descripción de cada uno de sus componentes. 

es usual que una mayor complejidad computacional venga asociada a este aumento en el grado de detalle del modelo.

Este nivel de complejidad del modelo resulta ser uno de los factores más importantes a la hora de decidir qué modelo realizar en un fenómeno epidémico (8,9). No obstante, la funcionalidad también es esencial a la hora de realizar un modelo, o dicho en otros términos, cuánto logra ajustarse a una necesidad específica. De hecho, existen dos facetas de la modelación epidemiológica bien señaladas por Vespignani, él precisa diferenciar los modelos propuestos en tiempos de paz, o cuando no hay emergencias sanitarias, de los modelos propuestos en tiempos de guerra, como lo es la coyuntura sanitaria actual (10). Se espera que los modelos propuestos en “tiempos de guerra” busquen dar respuestas inmediatas al evento epidemiológico en curso, el pronóstico y la simulación de escenarios sopados bajo una complejidad computacional accesible, se convierten en objetivos esenciales para el modelador. En “tiempos de paz”, el modelador se puede dar la libertad de incluir más elementos en el modelo y pensarlo en términos de descripciones detalladas de las dinámicas epidémicas, sin la pretención de que deban ser útiles bajo un contexto específico y sin escatimar recursos computacionales.
Tipos de modelos epidemiológicos

De manera general se pueden clasificar los modelos compartimentales en cuatro grandes grupos de tipos de modelos: los modelos basados en datos, los modelos compartimentales dinámicos, los modelos basados en agentes y los modelos estocásticos. En la tabla 1 se muestran las principales características de cada uno de estos modelos, su funcionalidad y algunas de sus limitaciones.

Modelo
Características
Funcionalidad
Limitaciones
Modelos basados en datos
Parten del análisis estadístico sobre los datos.
Pronóstico de casos, mortalidad y demandas hospitalarias. 
Sirven para hacer predicción a escalas temporales bajas.
Parte del supuesto de que las tendencias estadísticas de los datos pueden describir las dinámicas futuras.
Modelos compartimentales dinámicos
La progresión de la enfermedad se representa con ecuaciones diferenciales sobre variables poblacionales.
Útiles para describir el grado de
Incertidumbre depende de entendimiento de historia natural y de contagio.
Al partir del supuesto de que los individuos son homogéneos no puede explicar fenómenos asociados a variabilidad individual como el fenómeno de superdispersión.
Modelos basados en agentes
La progresión ocurre a nivel individual y el contagio es explícitamente descrito.
Útiles para describir las dinámicas de contagio y de movilidad de los individuos o de agrupaciones de individuos
Su grado alto de detalle lleva a que  necesiten entradas y a que demanden una alta capacidad computacional 


Modelos estocásticos
Los cambios en las variables de estado dependen de probabilidades asignadas.
Suelen ser muy útiles para descubrir las probabilidades de distribución de variables desconocidas. Permite describir procesos epidémicos en poblaciones pequeñas o iniciando un brote (Yan and Chowell 2019)
El error asociado a los valores simulados depende del número de simulaciones.
Requiere mayor capacidad de computo


Tabla XX. 


En este capítulo se realizará una descripción detallada de los modelos clásicos compartimentales y sus variaciones. De igual manera, se abordaran los modelos basados en agentes (MBA).


## Referencias

<a id="ref1">1</a>: Frigg R, Hartmann S. Models in Science. In: Zalta EN, editor. The Stanford Encyclopedia of Philosophy [Internet]. Spring 2020. Metaphysics Research Lab, Stanford University; 2020. Available at: https://plato.stanford.edu/archives/spr2020/entries/models-science/  
    [↩](#backref1)

<a id="ref2">2</a>: Peschard I. Making sense of modeling: beyond representation. Eur J Philos Sci. 2011 Oct;1(3):335–52.  
    [↩](#backref2)

<a id="ref3">3</a>: Brauer F, Castillo-Chavez C, Feng Z. Simple compartmental models for disease transmission. In: Texts in Applied Mathematics. New York, NY: Springer New York; 2019. p. 21–61. (Texts in applied mathematics).  
    [↩](#backref3)

<a id="ref4">4</a>: Anderson W. The history in epidemiology. Int J Epidemiol. 2019 Jun 1;48(3):672–4.  
    [↩](#backref4)

<a id="ref5">5</a>: Bacaër N. Ross and malaria (1911). In: A Short History of Mathematical Population Dynamics. London: Springer London; 2011. p. 65–9.  
    [↩](#backref5)

<a id="ref6">6</a>: Bacaër N. McKendrick and Kermack on epidemic modelling (1926–1927). In: A Short History of Mathematical Population Dynamics. London: Springer London; 2011. p. 89–96.  
    [↩](#backref6)

<a id="ref7">7</a>: Weiss H (howie). The SIR model and the Foundations of Public Health. Materials . 2013;0001–17.  
    [↩](#backref7)

<a id="ref8">8</a>: Bacaer N. A short history of mathematical population dynamics. 2011th ed. London, England: Springer; 2010. 160 p.  
    [↩](#backref8)

<a id="ref9">9</a>: Brooks RJ, Tobias AM. Choosing the best model: Level of detail, complexity, and model performance. Math Comput Model. 1996 Aug;24(4):1–14.  
    [↩](#backref9)

<a id="ref10">10</a>: Vespignani A, Tian H, Dye C, Lloyd-Smith JO, Eggo RM, Shrestha M, et al. Modelling COVID-19. Nat Rev Phys. 2020 Jun;2(6):279–81.  
    [↩](#backref10)

<a id="ref11">11</a>: Rahimi I, Chen F, Gandomi AH. A review on COVID-19 forecasting models. Neural Comput Appl. 2021 Feb 4;1–11.
    [↩](#backref11)

<a id="ref12">12</a>: Brauer F, Castillo-Chavez C, Feng Z. Endemic disease models. In: Texts in Applied Mathematics. New York, NY: Springer New York; 2019. p. 63–116. (Texts in applied mathematics).  
    [↩](#backref12)

<a id="ref13">13</a>: Panovska-Griffiths J, Kerr CC, Waites W, Stuart RM. Mathematical modeling as a tool for policy decision making: Applications to the COVID-19 pandemic. In: Handbook of Statistics. Elsevier; 2021. p. 291–326. (Handbook of statistics).  
    [↩](#backref13)

<a id="ref14">14</a>: Massonis G, Banga JR, Villaverde AF. Structural identifiability and observability of compartmental models of the COVID-19 pandemic. Annu Rev Control [Internet]. 2020 Dec 21; Available from: http://dx.doi.org/10.1016/j.arcontrol.2020.12.001  
    [↩](#backref14)

<a id="ref15">15</a>: Pourmalek F, Rezaei Hemami M, Janani L, Moradi-Lakeh M. Rapid review of COVID-19 epidemic estimation studies for Iran. BMC Public Health. 2021 Feb 1;21(1):257.  
    [↩](#backref15)

<a id="ref16">16</a>: Keeling MJ, Rohani P. Modeling Infectious Diseases in Humans and Animals. Princeton University Press; 2008. 366 p.  
    [↩](#backref16)

<a id="ref17">17</a>: Piqueira JRC. Rumor propagation model: An equilibrium study. Math Probl Eng. 2010;2010:1–7.  
    [↩](#backref17)

<a id="ref18">18</a>: Brauer F, van den Driessche P, Wu J. Mathematical Epidemiology. Springer Science & Business Media; 2008. 414 p.  
    [↩](#backref18)

<a id="ref19">19</a>: Yan P, Chowell G. Quantitative Methods for Investigating Infectious Disease Outbreaks [Internet]. Texts in Applied Mathematics. 2019. Available from: http://dx.doi.org/10.1007/978-3-030-21923-9  
    [↩](#backref19)

<a id="ref20">20</a>: Guan J, Wei Y, Zhao Y, Chen F. Modeling the transmission dynamics of COVID-19 epidemic: a systematic review. J Biomed Res. 2020 Oct 30;34(6):422–30.  
    [↩](#backref20)

<a id="ref21">21</a>: Pribylova L, Hajnova V. SEIAR model with asymptomatic cohort and consequences to efficiency of quarantine government measures in COVID-19 epidemic [Internet]. 2020 [cited 2021 Mar 31]. Available from: http://arxiv.org/abs/2004.02601  
    [↩](#backref21)

<a id="ref22">22</a>: Victor Okhuese A. Estimation of the Probability of Reinfection With COVID-19 by the Susceptible-Exposed-Infectious-Removed-Undetectable-Susceptible Model. JMIR Public Health Surveill. 2020 May 13;6(2):e19097.  
    [↩](#backref22)

<a id="ref23">23</a>: Zhao S, Chen H. Modeling the epidemic dynamics and control of COVID-19 outbreak in China. Quant Biol. 2020 Mar 11;1–9.  
    [↩](#backref23)

<a id="ref24">24</a>: Giordano G, Blanchini F, Bruno R, Colaneri P, Di Filippo A, Di Matteo A, et al. Modelling the COVID-19 epidemic and implementation of population-wide interventions in Italy. Nat Med. 2020 Jun;26(6):855–60.  
    [↩](#backref24)

<a id="ref25">25</a>: Fosu GO, Opong JM, Appati JK. Construction of compartmental models for COVID-19 with quarantine, lockdown and vaccine interventions. SSRN Electron J [Internet]. 2020; Available from: https://www.ssrn.com/abstract=3574020  
    [↩](#backref25)

<a id="ref26">26</a>: Chen S, Robinson P, Janies D, Dulin M. Four Challenges Associated With Current Mathematical Modeling Paradigm of Infectious Diseases and Call for a Shift. Open Forum Infect Dis. 2020 Aug;7(8):ofaa333.  
    [↩](#backref26)

<a id="ref27">27</a>: Railsback SF, Grimm V. Agent-Based and Individual-Based Modeling: A Practical Introduction, Second Edition. Princeton University Press; 2019.  
    [↩](#backref27)

<a id="ref28">28</a>: Cuevas E. An agent-based model to evaluate the COVID-19 transmission risks in facilities. Comput Biol Med. 2020 Jun;121:103827.  
    [↩](#backref28)

<a id="ref29">29</a>: Hoertel N, Blachier M, Blanco C, Olfson M, Massetti M, Rico MS, et al. A stochastic agent-based model of the SARS-CoV-2 epidemic in France. Nat Med. 2020 Sep;26(9):1417–21.  
    [↩](#backref29)

<a id="ref30">30</a>: Panovska-Griffiths J, Kerr CC, Waites W, Stuart RM. Mathematical modeling as a tool for policy decision making: Applications to the COVID-19 pandemic [Internet]. Handbook of Statistics. 2021. p. 291–326. Available from: http://dx.doi.org/10.1016/bs.host.2020.12.001  
    [↩](#backref30)

<a id="ref31">31</a>: Truszkowska A, Behring B, Hasanyan J, Zino L, Butail S, Caroppo E, et al. COVID‐19 Modeling: High‐Resolution Agent‐Based Modeling of COVID‐19 Spreading in a Small Town (Adv. Theory Simul. 3/2021) [Internet]. Vol. 4, Advanced Theory and Simulations. 2021. p. 2170005. Available from: http://dx.doi.org/10.1002/adts.202170005  
    [↩](#backref31)

<a id="ref32">32</a>: Gaudou B, Huynh NQ, Philippon D, Brugière A, Chapuis K, Taillandier P, et al. COMOKIT: A Modeling Kit to Understand, Analyze, and Compare the Impacts of Mitigation Policies Against the COVID-19 Epidemic at the Scale of a City [Internet]. Vol. 8, Frontiers in Public Health. 2020. Available from: http://dx.doi.org/10.3389/fpubh.2020.563247  
    [↩](#backref32)

<a id="ref33">33</a>: Mahdizadeh Gharakhanlou N, Hooshangi N. Spatio-temporal simulation of the novel coronavirus (COVID-19) outbreak using the agent-based modeling approach (case study: Urmia, Iran). Inform Med Unlocked. 2020 Jul 30;20:100403.  
    [↩](#backref33)
