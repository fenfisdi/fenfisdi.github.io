**Tabla de contenido**

1. Descripción de los modelos compartimentales disponibles

    1. Modelo SIR

    2. Modelo SEIR

    3. Modelo SEIRV

2. Características de las variables de estado de los modelos

    4. Susceptibles (S)** **

    5. Expuestos (E)

    6. Infectados (I)

    7. Recuperados (R)

    8. Virus (V)

3. Descripción de los parámetros de cada modelo

    9. Modelo SIR

        1. Tasas de entrada al sistema / Proporción de Natalidad

        2. Proporción de muerte natural / Tasa de salidas del sistema

        3. Proporción de muerte debida a la enfermedad

        4. Tasa de transmisión 

        5. Tasa de vacunación 

        6. Tasa de recuperación 

        7. Tasa de reinfección

        8. Tasa de pérdida de inmunidad

    10. Modelo SEIR

        9. Tasa de entradas al sistema / Proporción de Natalidad

        10. Proporción de muerte natural / Tasa de salidas del sistema

        11. Periodo de incubación

        12. Tasa de muerte debida a la enfermedad

        13. Tasa de vacunación 

        14. Tasa de recuperación 

        15. Constante de transmisión entre S y E

        16. Constante de transmisión entre S e I

    11. Modelo SEIRV

        17. Proporción de Natalidad

        18. Proporción de muerte natural

        19. Periodo de incubación 

        20. Proporción de muerte debida a la enfermedad

        21. Tasa de recuperación 

        22. Tasa de dispersión del virus por personas Expuestas

        23. Tasa de dispersión del virus por personas Infectadas

        24. Tasa de remoción del virus

        25. Constante de transmisión entre S y E

        26. Constante de transmisión entre S e I

        27. Constante de transmisión entre S y V

        28. Coeficiente de ajuste de transmisión 

4. Instrucciones para realizar la simulación

    12. Tipos de simulación

        29. Parámetros fijos

        30. Ajuste de parámetros 

    13. Fuentes de datos

        31. Datos propios

        32. Datos del INS para COVID19

5. Consideraciones matemáticas de los modelos

6. Cómo interpretar los resultados del modelo 

    14. Archivos finales de la plataforma

7. Observaciones adicionales del equipo FenFiSDi. 

1. **Descripción de los modelos compartimentales**

Los modelos compartimentales son modelos dinámicos útiles para describir la transmisión de enfermedades muy usados en epidemiología. Ellos dividen la población en compartimentos, los cuales corresponden a una variable de estado que indica la cantidad de individuos que se encuentran en una etapa específica de la enfermedad [[1]](https://paperpile.com/c/GKx5pD/vLID). También  realizan supuestos sobre la naturaleza y velocidad a la cual se mueven de un compartimento a otro en el tiempo [[2]](https://paperpile.com/c/GKx5pD/PGRg); y son útiles para predecir tendencias y evaluar medidas de control [[3]](https://paperpile.com/c/GKx5pD/0TUf). En estos modelos se asume que [[4]](https://paperpile.com/c/GKx5pD/bQoV):

* Hay una mezcla homogénea de la población en el sentido de que la probabilidad de que un individuo haga contacto con todos los otros individuos de la población es la misma independientemente del compartimiento al que pertenezcan, en otras palabras, todos los individuos están igualmente distribuidos en el espacio.

* Todos los individuos susceptibles son igualmente susceptibles.

* Todos los individuos infecciosos son igualmente infecciosos independientemente de cuándo fue infectado un individuo o cuánto tiempo lleva infectado.

 A continuación se presenta una descripción de los modelos usados en esta plataforma: 

1. **Modelo SIR**

El modelo SIR es el modelo más básico para describir la transmisión de una enfermedad que confiere inmunidad contra reinfección [[2]](https://paperpile.com/c/GKx5pD/PGRg). Este modelo clasifica a los individuos en tres compartimentos: Susceptibles (S), Infectados (I) y recuperados (R), (ver descripción más adelante), dependiendo de los supuestos del modelo, este puede tener o no, en cuenta la tasa de natalidad y mortalidad de la población, la tasa de muerte por la enfermedad o la tasa de vacunación. **Nota: **En infecciones en las que un individuo infectado atraviesa su período infeccioso y se recupera sin adquirir inmunidad, se debe utilizar un modelo SIS. También puede suceder que los individuos recuperados vuelvan a sustituir la población de susceptibles a través de un mecanismo de pérdida de inmunidad, mientras la población misma es cerrada, en este caso se tiene un modelo tipo SIRS [[2]](https://paperpile.com/c/GKx5pD/PGRg). Las enfermedades causadas por virus pueden usualmente ser descritas por modelos tipo SIR [[2]](https://paperpile.com/c/GKx5pD/PGRg). 

2. **Modelo SEIR**

Los compartimentos del modelo SEIR son: Susceptibles (S), Expuestos (E), Infectados (I) y recuperados (R). Este modelo tiene un compartimento adicional al modelo SIR que son los Expuestos (E), cuyos individuos están infectados, pero no son capaces de transmitir la infección a los individuos susceptibles a través de contacto [[4]](https://paperpile.com/c/GKx5pD/bQoV), por lo tanto, los individuos expuestos (E) transitan a los individuos Infectados (I) cuando se vuelven infecciosos (periodo latente), y puede que aún no hayan manifestado síntomas. Este compartimiento E permite describir la enfermedad de manera más exacta, ya que el periodo de incubación es diferente del periodo latente [[1]](https://paperpile.com/c/GKx5pD/vLID).

La diferencia entre el periodo de incubación y el periodo de latencia, denotada con el término ω [[5]](https://paperpile.com/c/GKx5pD/abUj), ver Figura 1, puede ser positiva para enfermedades infecciosas en las cuales la latencia es menor a la incubación. Los contagios por parte de personas infecciosas presintomáticas reciben el nombre de contagios subclínicos. Enfermedades infecciosas como el COVID-19 o más notoriamente el VIH presentan este comportamiento. Otro posible escenario infeccioso es cuando ω es negativo, esto ocurre cuando la incubación es más corta que la latencia y se presenta en enfermedades como el SARS en el que la mayoría de infecciones ocurren cuando personas susceptibles están en contacto con infectados en momentos tardíos de su enfermedad [[6]](https://paperpile.com/c/GKx5pD/MsAy), estas infecciones reciben el nombre de infecciones clínicas. Una última posibilidad es que la latencia y la incubación duren aproximadamente lo mismo donde ω es igual a cero, un caso representativo de este tipo de enfermedades infecciosas es la viruela en donde el inicio de síntomas es señal clara de inicio de infecciosidad [[7]](https://paperpile.com/c/GKx5pD/Ps8r). **Nota: **A pesar de que para el COVID-19 se ha discutido que las personas infectadas comienzan a ser infecciosas antes de presentar síntomas (ω positivo), no se ha logrado determinar la duración exacta de ese periodo latente, por lo tanto algunos modelos asumen que el periodo latente es igual al periodo de incubación.

Fig 1. La diferencia entre el periodo de incubación y el periodo de latencia está descrita con el término ω y puede tener uno de tres comportamientos: **A.** ω>0: los síntomas inician luego de que inicia la infecciosidad, esto lleva a la existencia de infecciones subclínicas. **B.** ω<0: los síntomas inician antes de que inicie la infecciosidad, todas las infecciones son clínicas. **C.** ω=0: los síntomas inician al mismo tiempo en el que inicia la infecciosidad.

3. **Modelo SEIRV**

Este es un modelos tipo SEIR con algunas modificaciones donde se considera que los individuos expuestos (E) están en el periodo de incubación, no muestran síntomas, pero pueden infectar a otras personas y los individuos infectados (I) son aquellos que han desarrollado completamente los síntomas de la enfermedad y también pueden contagiar o infectar a otros. El compartimento adicional al modelo SEIR que es el virus (V) representa la concentración  de este en el ambiente. Este modelo divide la población en cinco clases de individuos: Susceptibles (S), Expuestos (E), Infectados (I), recuperados (R) y Virus (V).

2. **Características de las variables de estado de los modelos**

1. **Susceptible (S): **Individuos que no tienen inmunidad y que pueden adquirir la infección a un ritmo determinado si entran en contacto con un individuo infeccioso [[8]](https://paperpile.com/c/GKx5pD/LCLV). 

2. **Expuesto (E): **Para el modelo SEIR son individuos que están infectados, pero no son capaces de transmitir la infección a otros individuos susceptibles a través de contactos [[4]](https://paperpile.com/c/GKx5pD/bQoV). Y los individuos permanecen en esta clase durante un periodo de tiempo llamado **periodo latente. **Para el modelo tipo SEIRV los individuos en la clase expuestos se encuentran en periodo de incubación, no muestran síntomas pero son capaces de infectar a otros, es decir, contienen individuos infecciosos asintomáticos.. En nuestro modelo SEIRV, los expuestos son individuos infecciosos pero asintomáticos.

 

3. **Infectado o infeccioso (I):** Para *el modelo SIR* son los individuos que transmiten la enfermedad a personas susceptibles y permanecen en esta clase durante un período de tiempo conocido como **período infeccioso**, antes de pasar a la clase recuperada o eliminada, [[6]](https://paperpile.com/c/GKx5pD/oNEa), Los individuos se vuelven infecciosos inmediatamente después de haber sido infectados, sin pasar por un periodo latente. Para *el modelo SEIR y SEIRV* son los individuos que han desarrollado completamente los síntomas de la enfermedad y pueden infectar a otras personas, en otras palabras son individuos infectados sintomáticos, que han iniciado su periodo infeccioso antes del inicio de síntomas [[7]](https://paperpile.com/c/GKx5pD/xMb4).

4. **Recuperado (R): **Indica el número de personas que se han infectado y sin probabilidad de volver a infectarse o de propagar la infección [[2]](https://paperpile.com/c/GKx5pD/PGRg). Entiéndase eliminan como: aislamiento del resto de la población, inmunización contra la infección (vacunas), inmunidad adquirida por recuperación de la enfermedad sin posibilidad de reinfección, muerte causada por la enfermedad [[2]](https://paperpile.com/c/GKx5pD/PGRg). 

5. **Virus (V): **Representa la concentración del virus en el reservorio ambiental. Este compartimento contempla el hecho de que los individuos susceptibles podrían contraer la enfermedad del ambiente contaminado [[10]](https://paperpile.com/c/GKx5pD/xMb4).

3. **Descripción de los parámetros de cada modelo**

Los parámetros en los modelos matemáticos, casi siempre están dados en términos de tasas. Entiéndase **tasa** como un cambio por unidad de tiempo, por ejemplo: metros por segundo, pulsaciones por minuto, infectados por día, etc., nos referimos a una razón dónde las unidades del denominador están dadas en tiempo. **Nota:** La definición de tasa usada acá, es diferente de la definición de tasa en epidemiología. 

    1. **Modelo SIR **(ver Fig 2)

        1. **Tasa de Natalidad/entradas al sistema**

La tasa de natalidad es la proporción de nacidos vivos en una población específica, con relación a la población total en un periodo de tiempo específico. **Nota**: Dado que el valor reportado tradicionalmente se da en términos de una tasa epidemiológica, es decir, está multiplicado por una constante en un periodo semestral o anual (ej. 1000, 10.000, 100.000), se debe realizar la división de la tasa de natalidad entre la constante y el número de días de un semestre o un año para obtener la proporción correcta que se ingresa al modelo. Por ejemplo: si tenemos una tasa de 25 nacidos vivos por cada 1000 habitantes de una región en particular en un año, entonces la proporción de natalidad es: 25/(1000 x 360) personas nacidas vivas/día = 0,0000694 personas nacidas vivas/día.

En este parámetro se pueden incluir o sumar a la tasa de natalidad, otras entradas al sistema, como la tasa de migración, o sea, el número de personas/día que llegan o entran a la población.

Si el usuario está usando parámetros fijos y se quiere simular un modelo SIR asumiendo un sistema cerrado sin cambios en la tasa de nacimientos y muertes naturales durante un periodo corto del brote, entonces se asigna un valor de cero a este parámetro. 

        2. **Tasa de muerte natural (por causas diferentes a la enfermedad de estudio)**

Proporción entre el número de defunciones en una población durante un año específico y la población total a mitad de año. **Nota**: Dado que este dato viene multiplicado por una constante y casi siempre es anual, se debe corregir de manera similar a las indicaciones dadas en la nota de proporción de natalidad. Si el usuario está usando parámetros fijos y no quiere tener en cuenta este parámetro, se le asigna un valor de cero.

        3. **Tasa de muerte debida a la enfermedad o tasa de fatalidad por caso (CFR):**

Proporción de personas que mueren por la enfermedad, entre el número de casos diagnosticados en un día [[11]](https://paperpile.com/c/GKx5pD/XVgN).

        4. **Tasa de transmisión: **

Velocidad a la cual un individuo susceptible se mueve al compartimento de infectados. Es calculado como el producto entre la tasa de contacto (número de contactos del sujeto) (*c*) y la probabilidad de que el contacto entre un individuo susceptible y un infectado resulte en una transmisión (*p*). Es decir: *tasa de transmisión* = *p *x *c **[[1*]](https://paperpile.com/c/GKx5pD/vLID). Usualmente recibe el nombre de 𝜷.

        5. **Tasa de vacunación **

Proporción de personas vacunadas (dosis completa) sobre la población total de un periodo de tiempo específico.** Nota:** Tener en cuenta hacer el ajuste del periodo de tiempo de la proporción por día. Si el usuario no quiere tener en cuenta este parámetro o no se tiene una vacuna disponible, se le asigna un valor de cero.

        6. **Tasa de recuperación**: 

Es el periodo de tiempo promedio que tarda un individuo en dejar de ser infeccioso, equivale al inverso del promedio del** periodo infeccioso** (tiempo promedio que un individuo permanece infectando a otros). Tasa de recuperación = 1/periodo infeccioso (1). En la literatura recibe el nombre de 𝜸.

        7. **Tasa de reinfección**

Proporción de personas que habiendo tenido la enfermedad (recuperadas) se infectan nuevamente por la misma enfermedad, es decir, número de individuos reinfectados entre el número total de individuos recuperados en un periodo de tiempo específico (día). **Nota**: En términos de los modelos compartimentales, son aquellas personas que pasan de un estado recuperado a infeccioso, nuevamente. Si el usuario está usando parámetros fijos y la enfermedad evaluada no presenta reinfección, se le asigna un valor de cero a este parámetro.

        8. **Tasa de pérdida de inmunidad**

Periodo de tiempo que tarda un individuo recuperado en volver a ser susceptible. Es equivalente al inverso del tiempo que tarda una persona en perder la inmunidad. Por ejemplo, si una persona tarda 180 días en perder la inmunidad, la tasa de pérdida de inmunidad será: 1/180 = 0.0055 días-1. **Nota:** Si el usuario está usando parámetros fijos y la enfermedad no presenta pérdida de inmunidad, se le asigna un valor de cero a este parámetro.

 ![image alt text](image_0.png)

Fig 2. Representación esquemática de modelo tipo SIR y algunos de sus posibles parámetros con dinámicas vitales. S representa a los susceptibles, I a los infectados y R recuperados. Las tasas de las dinámicas vitales están representadas por la flecha verde (natalidad) y flechas rosadas (mortalidad no asociada a la enfermedad modelada), la tasa de transmisión está representada por la flecha β, la tasa de recuperación por la flecha γ, la tasa de reinfección está representada por la flecha con origen en R dirigida a I , la tasa de vacunación por la flecha azul y la flecha roja representa la CFR o tasa de mortalidad por la enfermedad.

    2. **Modelo SEIR **(ver Fig 3)

        9. **Tasa de Natalidad**

Proporción de nacidos vivos en una población específica, con relación a la población total en un periodo de tiempo específico. **Nota**: Dado que el valor reportado tradicionalmente se da en términos de una tasa, es decir, está multiplicado por una constante en un periodo semestral o anual (ej. 1000, 10.000, 100.000), se debe realizar la división de la tasa de natalidad entre la constante y el número de días de un semestre o un año para obtener la proporción correcta que se ingresa al modelo. Por ejemplo: si tenemos una tasa de 25 nacidos vivos por cada 1000 habitantes de una región en particular en un año, entonces la proporción de natalidad es: 25/(1000 x 360) personas nacidas vivas/día = 0,0000694 personas nacidas vivas/día.

En este parámetro se pueden incluir o sumar a la tasa de natalidad, otras entradas al sistema, como la tasa de migración, osea, el número de personas/día que llegan o entran a la población.

Si el usuario está usando parámetros fijos y se quiere simular un modelo SIR asumiendo un sistema cerrado sin cambios en la tasa de nacimientos y muertes naturales durante un periodo corto del brote, entonces se asigna un valor de cero a este parámetro. 

        10. **Tasa de mortalidad por causas diferentes a la enfermedad**

Proporción entre el número de defunciones en una población durante un año específico y la población total a mitad de año. **Nota**: Dado que este dato viene multiplicado por una constante y casi siempre es anual, se debe corregir de manera similar a las indicaciones dadas en la nota de proporción de natalidad. Si el usuario está usando parámetros fijos y no quiere tener en cuenta este parámetro, se le asigna un valor de cero.

        11. Periodo de latencia: Es el periodo

        12. **Periodo de incubación **

Es el tiempo transcurrido entre la infección de un individuo por un patógeno y la manifestación de los síntomas (días) [[12]](https://paperpile.com/c/GKx5pD/SZgR). Acá se debe tener en cuenta que para muchas enfermedades infecciosas, el periodo de incubación es igual al **periodo latente **(Período desde que el individuo es infectado con el patógeno hasta que se vuelve infeccioso), es decir, que el individuo comienza a ser infeccioso en el momento mismo que manifiesta los síntomas [[13]](https://paperpile.com/c/GKx5pD/bMN4). **Nota: **En el caso de la COVID-19 el periodo latente es diferente del periodo de incubación, es decir, que los individuos comienzan a ser infecciosos antes del inicio de síntomas. 

        13. **Tasa de muerte debida a la enfermedad o tasa de fatalidad por caso (CFR)**

La tasa de fatalidad por caso (CFR por sus siglas en inglés) es calculado como la proporción de personas que mueren por la enfermedad, entre el número de casos diagnosticados en un día [[11]](https://paperpile.com/c/GKx5pD/XVgN).

        14. **Tasa de vacunación **

Proporción de personas vacunadas (dosis completa) sobre la población total, en un periodo de tiempo específico.** Nota:** Tener en cuenta hacer el ajuste del periodo de tiempo de la proporción por día.

Si el usuario no quiere tener en cuenta este parámetro o no se tiene una vacuna disponible, se le asigna un valor de cero.

        15. **Tasa de recuperación**: 

Es el periodo de tiempo promedio que tarda un individuo en recuperarse después del inicio de síntomas , equivale al inverso del promedio del** periodo infeccioso** (tiempo promedio que un individuo permanece infectando a otros). Tasa de recuperación = 1/periodo infeccioso (por día) [[1]](https://paperpile.com/c/GKx5pD/vLID). 

        16. **Constante de transmisión de E a S**

Valor máximo (Constante positiva) de la velocidad de transmisión de la infección entre los individuos expuestos y los susceptibles, es decir, número máximo de individuos susceptibles (S) que un individuo expuesto (E) puede infectar por día (personas/ día). **Nota: **Para este parámetro se asume que los individuos en el compartimento Expuestos (E) comienzan a ser infecciosos antes de ingresar a la clase Infectados (I), si este no es el caso de la enfermedad a simular, se le asigna un valor de cero. Para el COVID-19 se recomienda que este parámetro sea ajustado.

        17. **Constante de transmisión de I a S**

Valor máximo de la velocidad de transmisión de la infección, entre los individuos infectados (I) y los susceptibles, es decir, número máximo de individuos susceptibles (S) que pueden ser infectados en un día por un individuo infectado (I) (personas/día). **Nota: **Para el COVID-19 se recomienda que este parámetro sea ajustado.

![image alt text](image_1.png)

**Fig 3.** Representación esquemática de modelo tipo SEIR y sus parámetros con dinámicas vitales. S representa a los susceptibles, E a los expuestos, I a los infectados y R recuperados. Las tasas de las dinámicas vitales están representadas por la flecha verde (natalidad) y flechas rosadas (mortalidad no asociada a la enfermedad modelada). La tasa de transmisión está representada por la flecha β, el periodo latente por la flecha κ, la tasa de recuperación por la flecha γ, la tasa de vacunación por la flecha azul y la flecha roja representa la CFR o tasa de mortalidad causada por la enfermedad.

    3. **Modelo SEIRV** (ver Fig 4.)

        18. **Proporción de Natalidad**

Proporción de nacidos vivos en una población específica, con relación a la población total en un periodo de tiempo específico. **Nota**: Dado que el valor reportado tradicionalmente se da en términos de una tasa, es decir, está multiplicado por una constante en un periodo semestral o anual (ej. 1000, 10.000, 100.000), se debe realizar la división de la tasa de natalidad entre la constante y el número de días de un semestre o un año para obtener la proporción correcta que se ingresa al modelo. Por ejemplo: si tenemos una tasa de 25 nacidos vivos por cada 1000 habitantes de una región en particular en un año, entonces la proporción de natalidad es: 25/(1000 x 360) personas nacidas vivas/día = 0,0000694 personas nacidas vivas/día.

        19. **Proporción de mortalidad por causas diferentes a la enfermedad**

Proporción entre el número de defunciones en una población durante un año específico y la población total a mitad de año (muertes/día). **Nota**: Este dato se obtiene de manera similar al reportado en la nota de proporción de natalidad.

        20. **Periodo de incubación:**

Es el tiempo transcurrido entre la infección de un individuo por un patógeno y la manifestación de los síntomas (días) [[12]](https://paperpile.com/c/GKx5pD/SZgR). Acá se debe tener en cuenta que para la mayoría de las enfermedades infecciosas, el periodo de incubación es igual al **periodo latente **(Período desde que el individuo es infectado con el patógeno hasta que se vuelve infeccioso), es decir, que el individuo comienza a ser infeccioso en el momento mismo que manifiesta los síntomas [[13]](https://paperpile.com/c/GKx5pD/bMN4) (Ej: SARS-CoV-1). **Nota: **En el caso de la COVID-19 el periodo latente es diferente del periodo de incubación, es decir, que los individuos comienzan a ser infecciosos antes del inicio de síntomas. 

Periodo

        21. **Proporción de muerte debida a la enfermedad (CFR)**

Proporción de personas que mueren por la enfermedad, entre el número de casos diagnosticados en un día .

        22. **Tasa de recuperación:** 

Es el periodo de tiempo promedio que tarda un individuo en dejar de ser infeccioso, equivale al inverso del promedio del **periodo infeccioso** (tiempo promedio que un individuo permanece infectando a otros) Tasa de recuperación = 1/periodo infeccioso (por día) [[1]](https://paperpile.com/c/GKx5pD/vLID). 

        23. **Tasa de dispersión del virus por personas Expuestas**

Es la concentración de virus que un individuo expuesto disemina al reservorio ambiental en un periodo de tiempo determinado (concentración de virus/día-persona). **Nota: **Para este parámetro se asume que los individuos en el compartimento expuestos (E) comienzan a ser infecciosos antes de ingresar a la clase infectados (I).

        24. **Tasa de dispersión del virus por personas Infectadas**

Es la concentración de virus que un individuo infectado disemina al reservorio ambiental en un periodo de tiempo determinado. Para el caso de una epidemia o pandemia donde los infectados son aislados, es decir, puestos en cuarentena en casa u hospitalizados, esta tasa de dispersión puede ser despreciable (concentración de virus/día-persona). 

        25. **Tasa de remoción del virus del ambiente:**

Es el inverso del tiempo de vida media del virus en el ambiente (por día). El virus puede estar presente en forma de aerosoles dispersos en el aire, cuya vida media depende de la humedad y la temperatura del ambiente, y también puede estar asentado en fomites (superficies metálicas, vidrio, madera, cartón, etc.). 

        26. **Constante de transmisión de E a S:**

Valor máximo (Constante positiva) de la velocidad de transmisión de la infección entre los individuos expuestos y los susceptibles, es decir, número máximo de individuos susceptibles (S) que un individuo expuesto (E) puede infectar por día (personas/ día). **Nota: **Para este parámetro se asume que los individuos en el compartimento expuestos (E) comienzan a ser infecciosos antes de ingresar a la clase infectados (I), si este no es el caso de la enfermedad a simular, se le asigna un valor de cero. Para el COVID-19 se recomienda que este parámetro sea ajustado.

        27. **Constante de transmisión de I a S:**

Valor máximo de la velocidad de transmisión de la infección, entre los individuos infectados (I) y los susceptibles. es decir, número máximo de individuos susceptibles (S) que pueden ser infectados en un día por un individuo infectado (I) (personas/ día). **Nota: **Para el COVID-19 se recomienda que este parámetro sea ajustado.

        28. **Constante de transmisión de V a S**

Valor máximo de la velocidad de transmisión indirecta, del ambiente a los humanos, osea, del virus a los individuos susceptibles. (Es una constante positiva que se obtiene por fijación de los datos; personas/día). **Nota: **Para el COVID-19 se recomienda que este parámetro sea ajustado.

        29. **Coeficientes de ajuste de transmisión**

Estos coeficientes de transmisión son ajustados de acuerdo con los datos disponibles. De acuerdo con este modelo, se tiene un coeficiente de transmisión para cada una de las velocidades de transmisión, es decir, hay dos coeficientes para la transmisión directa, humano a humano, entre los individuos expuestos y susceptibles, e infectados y susceptibles; y uno para la transmisión indirecta, ambiente a humano, entre el virus del ambiente y los individuos susceptibles (adimensional). 

 

![image alt text](image_2.png)

**Fig 4.** Representación esquemática de modelo tipo SEIRV y algunos de sus parámetros con dinámicas vitales. S representa a los susceptibles, E a los expuestos, I a los infectados, R recuperados y V el virus en el ambiente. Las tasas de las dinámicas vitales están representadas por la flecha verde (natalidad) y flechas rosadas (mortalidad no asociada a la enfermedad modelada). La tasa de transmisión está representada por la flecha β (al asumirse que los expuestos pueden infectar, esto es que la incubación es mayor que la latencia, ω>1, β depende de la constante de infección de I a S, de E a S y de V a S),  el periodo latente por la flecha κ, la tasa de recuperación por la flecha γ, la tasa de vacunación por la flecha azul, la flecha roja representa la CFR o tasa de mortalidad causada por la enfermedad y las flechas moradas representan la diseminación viral en el ambiente (los Expuestos son considerados infecciosos (ω>1)

4. **Instrucciones para realizar la simulación**

El interesado en utilizar los modelos SIR, SEIR y SEIRV para estudiar escenarios posibles de la propagación de una enfermedad infecciosa deberá contar con la información suficiente sobre el sistema que pretende estudiar, ya que la elección de las variables de estado y los parámetros dependen del objetivo del modelo. Asimismo, se recomienda al usuario consultar si hay datos disponibles del sistema (datos reales) ya que en esta plataforma podrá ajustar los parámetros que desee a series de tiempo experimentales. 

1. **Tipos de simulación**

El usuario puede elegir entre dos tipos de simulaciones, parámetros fijos o ajuste de parámetros, tal que diseñe el modelo de acuerdo a la información y los datos disponibles. Nótese que es posible tener algunos parámetros fijos y otros ajustados, pues el usuario puede elegir cuales desea ajustar a los datos que utilice y cuales tendrán un valor numérico definido por él.

    1. **Parámetros fijos**

Este tipo de simulación permite al usuario asignar un valor numérico a los parámetros del modelo elegido (ver sección parámetros). 

"RECORDAR: agregar la estructura de imágenes + texto con instrucciones de uso" 

    2. **Ajuste de parámetros**

Este tipo de simulación permite al usuario elegir qué parámetros del modelo elegido desea ajustar, usando un algoritmo evolutivo de optimización a los datos que seleccione entre las fuentes de datos disponibles. 

"RECORDAR: agregar la estructura de imágenes + texto con instrucciones de uso" 

2. **Fuentes de datos** 

Si el usuario elige el tipo de simulación ajuste de parámetros, deberá tener en cuenta que los datos a los cuales se ajustarán los parámetros de su modelo deben ser series de tiempo de una de las variables de estado. Dichas series de tiempo tendrán un orden cronológico dado por la escala temporal del modelo (ej días, horas, semanas, etc)

    3. **Datos propios **

El usuario que elige la opción de ingresar datos propios debe tener en cuenta el formato sugerido para la correcta lectura de los datos. 

"RECORDAR: agregar imagen del formato y tipos de archivos"

    4. **Datos del INS para COVID19**

Teniendo en cuenta la emergencia sanitaria por COVID19 en Colombia, el Instituto Nacional de Salud construyó una estrategia para el registro y rastreo de todos los casos positivos de COVID19 desde la detección del primer infectado en marzo 3 de 2020 (agregar referencia). 

"RECORDAR: agregar la estructura de imágenes + texto con instrucciones de uso"

**5. Consideraciones matemáticas**

**Objective functions:**

Objective functions define an optimization goal and aim to maximize or minimize certain values associated to a set of design responses or solutions.

An optimization problem can be stated as: max(Φ(U(x),x)) , where Φ is the objective function that depends on the state variables, U , and the design variables, x .

**Evolutionary algorithm for parameter optimization**

Evolutionary algorithms are population-based stochastic search algorithms that optimize solutions iteratively. This family of algorithms explores the solution space maintaining candidate solutions and creating new ones from processes of mutation and crossover of existing solutions. 

In evolutionary algorithms, variables for optimization are assumed as vectors that goes through four stages. The first stage is the **initialization **stage where the first generation of solutions is created randomly from a range between minimal and maximal possible variable values. Next, in the **mutation** stage, new random vectors are created from initial vectors. Then, at the **crossover** stage, each mutated vector is crossed with its original vector with a specific probability. The performance of both vectors, the initial and its altered counterpart, is compared and the fittest is selected (**selection** stage). The process is repeated across several generations until the population as a whole surpasses a certain fitness threshold.

Evolutionary algorithms only depend on three control parameters: population size, mutation strength and crossover probability.

Georgioudakis, Manolis, and Vagelis Plevris. 2020. "A Comparative Study of Differential Evolution Variants in Constrained Structural Optimization." Frontiers in Built Environment 6 (July). https://doi.org/10.3389/fbuil.2020.00102.

**The initial value problem**

The initial value problem is a differential equations y’(t) = f(t,y(t)) with a point in the domain of f (t0,y0) which is the initial condition.

A solution to an initial value problem is a function y that is a solution to the differential equation satisfying:

y0(t0) = y0

In higher orders, initial value problems are extended by considering derivates as independent functions, e.g. y’’(t) = f(t,y(t),y’’(t)), and giving the appropriate number of initial conditions.

**Numerical methods for differential equations:**

Numerical methods are used to approximate solutions for differential equations when analytical solutions are hard or impossible to calculate. There are several methods and they are grouped in one-step methods, multistep methods and finite differences methods. 

One of the best known multi-step methods are the Runge-Kutta methods. They work by averaging the slope of tangent lines at different points within a specific range. Differences between Runge-Kutta methods come from the number of steps, the way steps are taken and how the error is controlled.

RK4 method is the most stable and easy to implement method among Runge-Kutta methods. This method considers four tangent segments (k1, k2, k3, k4) with their slopes calculated as follows (2, 3): 

* k1: based on the slope at the beginning of the interval, using y.

* k2: based on the slope at the midpoint of the interval, using y + hk1/2.

* k3: based on the slope at the midpoint too, but using y + hk2/2.

* k4: based on the slope at the end of the interval, using y + hk3.

The midpoint segments are weighted when all the segments are averaged.

2. Denis, B. 2012 An overview of numerical and analytical methods for solving ordinary differential equations. https://arxiv.org/abs/2012.07558

3. https://www.geeksforgeeks.org/runge-kutta-4th-order-method-solve-differential-equation/

**----------------------------------------------------------------------------------- English Version----------------**

**Text for the platform of compartmental models**

 

**Table of contents**

    1. Description of the available compartment models

            1. SIR model

            2. SEIR model

            3. SEIRV model

    2. Characteristics of the state variables of the models

1. Susceptible (S)

2. Exposed (E)

3. Infected (I)

4. Recovered (R)

5. Virus (V)

3. Description of the parameters of each model

            1.  SIR model

i. System entry rate / Birth rate

ii. Natural death rate / Rate of exit from the system

iii. Disease-induced death rate

iv. Transmission rate

v. Vaccination rate

vi. Recovery rate

vii. Reinfection rate

viii. Immunity loss rate

b. SEIR model

i. System entry rate / Birth rate

ii. Rate of natural death / Rate of exits from the system

iii. Incubation period

iv. Disease-induced death rate

v. Vaccination rate

vi. Recovery rate

vii. Transmission constant from E to S 

viii. Transmission constant from I to S

c. SEIRV model

i. Birth rate

ii. Natural death rate

iii. Incubation period

iv. Disease-induced death rate

v. Recovery rate

vi. Virus spread rate by exposed people

vii. Virus spread rate by infected people

viii. Virus removal rate

ix. Transmission constant from E to S

x. Transmission constant between S and I

xi. Transmission constant from S to V

xii. Transmission adjustment coefficient

	4. Instructions to perform the simulation

a. Simulation types

i. Fixed parameters

ii. Setting parameters

b. Data sources

     		i. Own data

ii. INS data for COVID-19

    1. How to interpret the results of the model

        1. Final platforms files

    2. Aditional observations from FenFisDi team

1. Description of the available compartment models

Compartmental models are useful dynamical models widely used in epidemiology to describe the transmission of infectious diseases. They divide the population into compartments, which correspond to state variables that indicates the number of individuals that are in a specific stage of the disease [1]. They also make assumptions about the nature and speed of transmission from one compartment to another in time [2]; and are useful for predicting trends and evaluating control measures [[3]](https://paperpile.com/c/GKx5pD/0TUf). In these models it is assumed that [(Yan and Chowell 2019)](https://paperpile.com/c/GKx5pD/bQoV):

* There is a homogeneous mixture of the population in the sense that the probability that an individual makes contact with all other individuals within the population is the same regardless of the compartment they are, in other words, all individuals are equally distributed in space.

* All susceptible individuals are equally susceptible.

* All infectious individuals are equally infectious.

See below a description of the models you will find in this platform:

1. **SIR model**

The SIR model is the most basic model to describe the transmission of a disease that confers immunity against reinfection [2]. In this model, the population is divided into three classes of individuals: Susceptible (S), Infected (I) and recovered (R). Depending on the assumptions of the model, the population's birth and death rate, the death rate from the disease, or the vaccination rate may or may not be taken into account. **Note:** In infections where an infected individual goes through his infectious period and recovers without acquiring immunity, a SIS model should be used. It can also happen that recovered individuals replace the susceptible population again through a mechanism of loss of immunity, while the population itself is closed, in this case there is a SIRS-type model [2]. Diseases caused by some viruses are usually of the SIR type [2].

2. **SEIR model **

Compartments of the SEIR model are: Susceptible (S), Exposed (E), Infected (I) and recovered (R). This model has an additional compartment to the SIR model, which is Exposed (E), whose individuals are infected, but are not able to transmit the infection to susceptible individuals through contacts [4], therefore, exposed individuals (E) move to Infected individuals (I) when they become infectious, and may not have manifested symptoms yet. This compartment E allows a more exact description of the disease, since the incubation period is different from the latent period [1]. Note: For COVID-19 it has been argued that infected people begin to be infectious before presenting symptoms, however, the exact duration of this latent period has not been determined, therefore some models assume that the latent period is equal to the incubation period.

Fig 1. The difference between the incubation period and the latent period is described by the term ω and may behave as follows: **A. **ω>0: symptoms begin after the onset of the infectious period, it leads to the existence of subclinical contagions. **B.** ω<0: symptom begin before the onset of the infectious period, i.e. all infectious are clinical  **C.** ω=0: symptoms begin at the same time infectiousness begins.

3. **SEIRV model**

This is an extension of the SEIR model, where individuals go through a period of exposure (E) between being infected and becoming infectious, with an additional compartment that is the Virus (V), which represents the concentration of virus particles in the environment. This model divides the population into five classes of individuals: Susceptible (S), Exposed (E), Infected (I), recovered (R) and Virus (V).

1. State variables characteristics

1. **Susceptible (S): **Individuals who do not have immunity and who can acquire the infection at a certain rate if they come into contact with an infectious individual [[8]](https://paperpile.com/c/GKx5pD/LCLV).

2. **Exposed (E): **They are individuals who are infected, but are not able to transmit the infection to other susceptible individuals through contacts [4]. Individuals remain in this class for a period of time called the **latent period**.

3. **Infectious: **They are individuals capable of spreading the disease by contact with susceptible people [2] and remain in this class for a period of time known as the **infectious period**, before moving to the recovered or eliminated class [6]. For the SIR model, individuals become infectious immediately after being infected, without going through a latent period, while for the SEIR and SEIRV model, individuals become infectious after having passed through a latent period.

4. **Recovered: **Indicates the number of people who have been infected without probability of re-infection or spreading the infection [2]. They are understood to be eliminated as: isolation from the rest of the population, immunization against infection (vaccines), immunity acquired by recovery from the disease without the possibility of reinfection, death caused by the disease [2].

5. **Virus: **Represents the concentration of the virus in the environmental reservoir. This compartment contemplates the fact that susceptible individuals could contract the disease from the contaminated environment [7].

3. Description of the parameters of each mode

Parameters in mathematical models are almost always given in terms of rates. Let’s understand rate as a change per unit of time, for example: meters per second, beats per minute, infected per day, etc., we refer to a ratio, where the units of the denominator are given in time. **Note:** The definition of rate used here is different from the definition of rate in epidemiology.

1. **SIR model**

                   **i.**    **Birth Rate:**

Proportion of individuals born alive in a specific population relative to the total population in a specific period. **Note:** Since the traditionally reported value is given in terms of a rate, i.e., it is multiplied by a constant in a semi-annual or annual period (e.g. 1000, 10,000, 100,000), the division of the birth rate must be performed between the constant and the number of days in a semester or a year to obtain the correct proportion that is entered into the model. For example: if we have a rate of 25 live births per 1000 inhabitants of a particular region in a year, then the birth rate is: 25 / (1000 x 360) live births / day = 0.0000694 live born people /day. 

This parameter can include or add to the birth rate, other inputs to the system, such as the migration rate, that is, the number of people / day that arrive to the population.

If the user is using fixed parameters and wants to simulate a SIR model assuming a closed system where there are no changes in births and natural deaths during a short period of the outbreak, then a value of zero is assigned to this parameter.

 

                  **ii.**   **Death rate not related to the disease**

Ratio between the number of deaths in a population during a specific year and the total population at the middle of the year. **Note:** Since this data is multiplied by a constant and is almost always annual, it must be corrected similarly to the indications given in the note on the birth rate. If the user is using fixed parameters and does not want to take this parameter into account, it is assigned a value of zero.

	 

                  **iii.**    **Disease-induced death rate or case fatality rate (CFR):**

It is calculated as the proportion of people who die from the disease, among the number of cases diagnosed in one day.

 

                  **iv.**    **Transmission rate:**

Rate at which a susceptible individual moves into the infected compartment. It is calculated as the product between the contact rate (number of contacts of the subject) (c) and the probability that contact between a susceptible individual and an infected individual results in transmission (p). i.e.: transmission rate = p x c [1].

 

                  **v.**    **Vaccination rate:**

Proportion of vaccinated people (full dose) over the total population for a specific period of time. **Note:** Take into account making the adjustment of the time period of the ratio per day. If the user does not want to take this parameter into account or if a vaccine is not available, it is assigned a value of zero.

 

                  **vi.**    **Recovery rate:**

It is the average period of time that it takes an individual to stop being infectious, it is equivalent to the inverse of the average of the infectious period (average time that an individual remains infecting others). Recovery rate = 1 / infectious period (1)

 

                 **vii.**    **Re-infection rate:**

Proportion of people who having had the disease (recovered) are infected again by the same disease, that is, the number of reinfected individuals among the total number of individuals recovered in a specific period of time (day). **Note:** In terms of compartmental models, they are those people who go from a recovered state to infections, again. If the evaluated disease does not present reinfection, a value of zero is assigned to this parameter.

 

                **viii.**    **Immunity loss rate:**

Period of time that it takes for a recovered individual to become susceptible again. It is equivalent to the inverse of the time it takes for a person to lose immunity. For example, if it takes a person 180 days to lose immunity, the rate of loss of immunity will be: 1/180 = 0.0055 days-1. **Note:** If the disease does not show loss of immunity, this parameter is assigned a value of zero.

![image alt text](image_3.png)

**Fig 1.** Schematic representation of a SIR type model and some of its possible parameters with vital dynamics. S represents Susceptible individuals, I infected and R recovered. Vital dynamic rates are represented as green arrows (birth rate) and pink arrows (death rate unrelated to the modeled disease). Transmission rate is represented as the β arrow, recovery rate as the γ arrow, reinfection rate as the arrow from R to I, vaccination rate as the blue arrow and the red arrow represents the CFR or the disease fatality rate. 

b. SEIR model

                   **i.**    **Birth Rate**

Proportion of individuals born alive in a specific population relative to the total population in a specific period. Note: Since the traditionally reported value is given in terms of a rate, that is, it is multiplied by a constant in a semi-annual or annual period (eg 1000, 10,000, 100,000), the division of the birth rate must be performed between the constant and the number of days in a semester or a year to obtain the correct proportion that is entered into the model. For example: if we have a rate of 25 live births per 1000 inhabitants of a particular region in a year, then the birth rate is: 25 / (1000 x 360) live births / day = 0.0000694 live born people /day. This parameter can include or add to the birth rate, other inputs to the system, such as the migration rate, that is, the number of people / day that arrive to the population.

If the user is using fixed parameters and wants to simulate a SIR model assuming a closed system where there are no changes in births and natural deaths during a short period of the outbreak, then a value of zero is assigned to this parameter.

 

                  **ii.**    ** Death rate not related to disease**

Ratio between the number of deaths in a population during a specific year and the total population at the middle of the year. **Note:** Since this data is multiplied by a constant and is almost always annual, it must be corrected similarly to the indications given in the note on the birth rate. If the user is using fixed parameters and does not want to take this parameter into account, it is assigned a value of zero.

 

                  **iii.**    **Incubation period:**

It is the average period of time between the infection of an individual by a pathogen and the manifestation of symptoms (days) [8]. Here it must be taken into account that for most infectious diseases, the incubation period is equal to the latent period (Period from when the individual is infected with the pathogen until it becomes infectious), that is, the individual begins to be infectious at the same time that symptoms appear (i.e. SARS-CoV-1). **Note:** In the case of COVID-19, the latent period is different from the incubation period, that is, individuals begin to be infectious before the onset of symptoms.

 

                  **iv.**   **Disease fatality rate (CFR):**

It is calculated as the proportion of people who die from the disease, among the number of cases diagnosed in one day.

 

                  **v.**    **Vaccination rate:**

Proportion of vaccinated people (full dose) over the total population, in a specific period of time. **Note:** Take into account making the adjustment of the time period of the ratio per day. If the user does not want to take this parameter into account or if a vaccine is not available, it is assigned a value of zero.

 

                  **vi.**    **Recovery rate:**

It is the average period of time that it takes an individual to stop being infectious, it is equivalent to the inverse of the average of the infectious period (average time that an individual remains infecting others). Recovery rate = 1 / infectious period (per day) (1). 

           

                 	**viii.** **Transmission constant between I to S:**

Maximum value of infection transmission rate, between the symptomatic infected (I) and the susceptible (S) individuals. That is, the maximum number of susceptible individuals (S) that can be infected per day by an infected individual (I) (person / day). **Note: **For COVID-19 it is recommended that this parameter be adjusted.

![image alt text](image_4.png)

**Fig 3. **Schematic representation of a SEIR type model and some of its possible parameters with vital dynamics. S represents susceptible individuals, E exposed, I infected and R recovered. Vital dynamic rates are represented as green arrows (birth rate) and pink arrows (death rate unrelated to the modeled disease). Transmission rate is represented as the β arrow, rate of progression from E to I is represented as the κ arrow, recovery rate as the γ arrow, reinfection rate as the arrow from R to I, vaccination rate as the blue arrow and the red arrow represents the CFR or the  disease fatality rate. 

c. SEIRV model

                   **i.**    **Birth Rate**

Proportion of individuals born alive in a specific population relative to the total population in a specific period. Note: Since the traditionally reported value is given in terms of a rate, that is, it is multiplied by a constant in a semi-annual or annual period (eg 1000, 10,000, 100,000), the division of the birth rate must be performed between the constant and the number of days in a semester or a year to obtain the correct proportion that is entered into the model. For example: if we have a rate of 25 live births per 1000 inhabitants of a particular region in a year, then the birth rate is: 25 / (1000 x 360) live births / day = 0.0000694 live born people /day.

This parameter can include or add to the birth rate, other inputs to the system, such as the migration rate, that is, the number of people / day that arrive to the population. If the user is using fixed parameters and wants to simulate a SIR model assuming a closed system where there are no changes in births and natural deaths during a short period of the outbreak, then a value of zero is assigned to this parameter.

** **

                  **ii.** **Death rate not related to disease**

Ratio between the number of deaths in a population during a specific year and the total population at the middle of the year. **Note:** Since this data is multiplied by a constant and is almost always annual, it must be corrected similarly to the indications given in the note on the birth rate. If the user is using fixed parameters and does not want to take this parameter into account, it is assigned a value of zero.

 

                  **iii.**    **Incubation period:**

It is the average period of time between the infection of an individual by a pathogen and the manifestation of symptoms (days) [8]. Here it must be taken into account that for most infectious diseases, the incubation period is equal to the latent period (Period from when the individual is infected with the pathogen until it becomes infectious), that is, the individual begins to be infectious at the same time that symptoms appear (i.e. SARS-CoV-1). **Note:** In the case of COVID-19, the latent period is different from the incubation period, that is, individuals begin to be infectious before the onset of symptoms.

 

                  **iv.**    **Disease-induced death rate or case fatality rate (CFR)**

It is calculated as the proportion of people who die from the disease, among the number of cases diagnosed in one day.

 

                  **v.**    **Recovery rate:**

It is the average period of time that it takes an individual to stop being infectious, it is equivalent to the inverse of the average of the infectious period (average time that an individual remains infecting others) (days-1).

 

                  **vi.**    **Virus shedding rate by exposed people:**

It is the concentration of virus that an exposed individual spreads to the environmental reservoir in a given period of time (virus / person-day).

 

                 **vii.**    **Virus shedding rate by infected people:**

It is the concentration of virus that an infected individual spreads to the environmental reservoir in a given period of time. In the case of an epidemic or pandemic where those infected are isolated, that is, quarantined at home or hospitalized, this rate of dispersal can be negligible (virus / person-day).

 

                **viii.**    **Removal rate of virus from the environment:**

It is the inverse of the half-life of the virus in the environment (per day). The virus can be present in the form of aerosols dispersed in the air, whose half-life depends on the humidity and temperature of the environment, and it can also be settled on fomites (metal surfaces, glass, wood, cardboard, etc.).

                 **ix. Transmission constant between S and E**

Maximum value (positive constant) of the infection transmission rate between the asymptomatic infected (exposed E) and susceptible individuals (S). That is, it is the maximum number of susceptible individuals (S) that an exposed individual (E) can infect per day (person / day). **Note: **For this parameter, it is assumed that the individuals in the exposed compartment (E) begin to be infectious before entering the infected class (I), if this is not the case of the disease to be simulated, a value of zero. For COVID-19 it is recommended that this parameter be adjusted.

    **  x. Transmission constant between S and I**

Maximum value of infection transmission rate, between the symptomatic infected (I) and the susceptible (S) individuals. That is, the maximum number of susceptible individuals (S) that can be infected per day by an infected individual (I) (person / day). **Note: **For COVID-19 it is recommended that this parameter be adjusted.

**    xi. Transmission constant between S and V**

Maximum value of the indirect, environment to human transmission rate, that is, of the virus to susceptible individuals. (It is a positive constant that is obtained by fixing the data; person / day). **Note: **For COVID-19 it is recommended that this parameter be adjusted.

**   xii. Transmission adjustment coefficient**

These transmission coefficients are adjusted according to the available data. According to this model, there is a transmission coefficient for each transmission rate, that is, there are two coefficients for direct transmission, human to human, between exposed and susceptible individuals, and infected and susceptible individuals; and one for indirect, environment-to-human transmission between the environmental virus and susceptible individuals (dimensionless).

![image alt text](image_5.png)

**Fig 4.** Schematic representation of a SEIR type model and some of its possible parameters with vital dynamics. S represents susceptible individuals, E exposed, I infected and R recovered. Vital dynamic rates are represented as green arrows (birth rate) and pink arrows (death rate unrelated to the modeled disease). Transmission rate is represented as the β arrow (since exposed individuals are able to infect, i.e. incubation is longer than latency ω>1, β depends on the infection constant from I to S, from E to S and from V to S), rate of progression from E to I is represented as the κ arrow, recovery rate as the γ arrow, reinfection rate as the arrow from R to I, vaccination rate as the blue arrow, the red arrow represents the CFR or the  disease fatality rate as purple arrows represent the viral shedding in the environment (exposed individuals are considered infectious ω>1).

4. **Instructions to perform the simulation**

The user interested in using the SIR, SEIR and SEIRV models to study possible scenarios of the spread of an infectious disease must have sufficient information about the system they want to study, since the choice of state variables and parameters depend on the objective of the model. Likewise, the user is recommended to check if there is data available from the system(real data) since in this platform you can adjust the parameters you want to experimental time series.

1. **Simulation types**

The user can choose between two types of simulations, fixed parameters or parameter adjustment, such that they design the model according to the information and data available. Note that it is possible to have some fixed parameters and others adjusted, since the user can choose which ones will be adjusted to data and which ones will have a numerical value defined by him.

**i. Fixed parameters**

This type of simulation allows the user to assign a numerical value to the parameters of the chosen model (see parameters section).

"RECORDAR: agregar la estructura de imágenes + texto con instrucciones de uso" 

**ii. Adjust parameters**

This type of simulation allows the user to choose which parameters of the chosen model he wishes to adjust, using an evolutionary algorithm for optimizing the data selected from the available data sources.

"RECORDAR: agregar la estructura de imágenes + texto con instrucciones de uso" >

2. **Data sources**

If the user chooses the simulation that requires the adjusted parameters, it must be taken into account that the data to which the parameters of that model will be adjusted must be time series of one of the state variables. These time series will have a chronological order given by the time scale of the model (eg days, hours, weeks, etc.)

**i. Upload data**

The user who chooses the option to enter their own data must take into account the suggested format for the correct reading of the data.

"RECORDAR: agregar imagen del formato y tipos de archivos"

**ii. Used available data (INS) for COVID-19**

Taking into account the health emergency due to COVID19 in Colombia, the National Institute of Health built a strategy for the registration and tracking of all positive cases of COVID19 since the detection of the first infected on March 3, 2020 (add reference).

"RECORDAR: agregar la estructura de imágenes + texto con instrucciones de uso"

**---------------------------------------------------------------------------------------------------------------------------**

Reference

1. 	[Massonis G, Banga JR, Villaverde AF. Structural identifiability and observability of compartmental models of the COVID-19 pandemic. Annu Rev Control. 2020. doi:](http://paperpile.com/b/GKx5pD/vLID)[10.1016/j.arcontrol.2020.12.001](http://dx.doi.org/10.1016/j.arcontrol.2020.12.001)

2. 	[Brauer F, van den Driessche P, Wu J. Mathematical Epidemiology. Springer Science & Business Media; 2008.](http://paperpile.com/b/GKx5pD/PGRg)

3. 	[Guan J, Wei Y, Zhao Y, Chen F. Modeling the transmission dynamics of COVID-19 epidemic: a systematic review. J Biomed Res. 2020;34: 422–430.](http://paperpile.com/b/GKx5pD/0TUf)

4. 	[Yan P, Chowell G. Quantitative Methods for Investigating Infectious Disease Outbreaks. Texts in Applied Mathematics. 2019. doi:](http://paperpile.com/b/GKx5pD/bQoV)[10.1007/978-3-030-21923-9](http://dx.doi.org/10.1007/978-3-030-21923-9)

5. 	[Arzt J, Branan MA, Delgado AH, Yadav S, Moreno-Torres KI, Tildesley MJ, et al. Quantitative impacts of incubation phase transmission of foot-and-mouth disease virus. Sci Rep. 2019;9: 2707.](http://paperpile.com/b/GKx5pD/abUj)

6. 	[SARS. 1 Apr 2021 [cited 6 May 2021]. Available: ](http://paperpile.com/b/GKx5pD/MsAy)[https://www.cdc.gov/sars/guidance/core/app1.html](https://www.cdc.gov/sars/guidance/core/app1.html)

7. 	[Smallpox. [cited 6 May 2021]. Available: ](http://paperpile.com/b/GKx5pD/Ps8r)[https://www.who.int/news-room/q-a-detail/smallpox](https://www.who.int/news-room/q-a-detail/smallpox)

8. 	[Prem K, Liu Y, Russell TW, Kucharski AJ, Eggo RM, Davies N, et al. The effect of control strategies to reduce social mixing on outcomes of the COVID-19 epidemic in Wuhan, China: a modelling study. Lancet Public Health. 2020;5: e261–e270.](http://paperpile.com/b/GKx5pD/LCLV)

9. 	[Katul GG, Mrad A, Bonetti S, Manoli G, Parolari AJ. Global convergence of COVID-19 basic reproduction number and estimation from early-time SIR dynamics. PLoS One. 2020;15: e0239800.](http://paperpile.com/b/GKx5pD/oNEa)

10. 	[Yang CY, Wang J. A mathematical model for the novel coronavirus epidemic in Wuhan, China. Math Biosci Eng. 2020;17: 2708–2724.](http://paperpile.com/b/GKx5pD/xMb4)

11. 	[Narayanan CS. A novel cohort analysis approach to determining the case fatality rate of COVID-19 and other infectious diseases. PLoS One. 2020;15: e0233146.](http://paperpile.com/b/GKx5pD/XVgN)

12. 	[Deng Y, You C, Liu Y, Qin J, Zhou X-H. Estimation of incubation period and generation time based on observed length-biased epidemic cohort with censoring for COVID-19 outbreak in China. Biometrics. 2020. doi:](http://paperpile.com/b/GKx5pD/SZgR)[10.1111/biom.13325](http://dx.doi.org/10.1111/biom.13325)

13. 	[Li Y-K, Zhao S, Lou Y-J, Gao D-Z, Yang L, He D-H. Epidemiological parameters and models of coronavirus disease 2019. Acta Physica Sinica. 2020. p. 090202. doi:](http://paperpile.com/b/GKx5pD/bMN4)[10.7498/aps.69.20200389](http://dx.doi.org/10.7498/aps.69.20200389)

