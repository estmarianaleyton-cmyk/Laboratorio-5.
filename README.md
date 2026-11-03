# Laboratorio-5

**Universidad Militar Nueva Granada**

**Asignatura:** Instrumentación biomedica y biosensores

**Estudiantes:** Dubrasca Martínez, Mariana Leyton, Joshara Valentina Palacios

**Fecha:** 28 de octubre del 2026

**Título de la práctica:** Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas

# **Introducción**

La monitorización continua de variables fisiológicas es una herramienta central en la atención clínica, porque permite detectar a tiempo el deterioro del paciente. Entre estas variables, la frecuencia cardíaca (FC) y la saturación periférica de oxígeno (SpO₂) están entre las más utilizadas. La FC refleja el ritmo de bombeo del corazón. La SpO₂ estima qué fracción de la hemoglobina arterial está transportando oxígeno [4], [5]. Condiciones como la bradicardia, la taquicardia o la hipoxemia pueden poner en riesgo inmediato al paciente. Por eso, los monitores de signos vitales deben medir estas variables con exactitud y, además, generar alarmas confiables cuando sus valores salen de los límites configurados. Estos requisitos están regulados por normas internacionales como la ISO 80601-2-61, para pulsioxímetros, y la IEC 60601-1-8, para sistemas de alarma en equipos electromédicos [7], [8].

La SpO₂ se mide de forma no invasiva mediante pulsioximetría. La técnica se basa en que la oxihemoglobina y la desoxihemoglobina absorben de manera diferente la luz roja (≈660 nm) y la infrarroja (≈940 nm). El sensor emite ambas longitudes de onda a través de un lecho vascular, normalmente el dedo, y un fotodetector registra la luz transmitida [4], [9]. Con cada latido, el volumen de sangre arterial aumenta y disminuye. Esto genera una componente pulsátil (AC) superpuesta a una componente constante (DC), que corresponde al tejido, la sangre venosa y la sangre arterial no pulsátil. Esa señal es la onda fotopletismográfica (PPG) que aparece en el monitor [6]. El equipo calcula el cociente de las relaciones AC/DC de ambas longitudes de onda, R = (AC_rojo/DC_rojo)/(AC_IR/DC_IR), y con una curva de calibración empírica lo convierte en un valor de SpO₂. La FC se obtiene a partir del intervalo entre pulsos consecutivos [4], [5]. Como la medición depende de una señal pulsátil adecuada, factores como la baja perfusión periférica, el movimiento o la luz ambiental pueden degradar la PPG y producir lecturas erróneas o falsas alarmas [4], [5]. Para cuantificar la calidad de la señal se usa el índice de perfusión (PI), que es la relación porcentual entre la componente pulsátil y la no pulsátil [1].

No es ético ni práctico inducir condiciones patológicas en pacientes para verificar el funcionamiento de un monitor. Por eso se usan simuladores de parámetros fisiológicos. El Pronk OxSim OX-1 es un simulador óptico de SpO₂ con un "dedo" fijo, que permite evaluar el sistema completo de pulsioximetría, incluido el sensor [2]. Su principio de funcionamiento consiste en captar la luz roja e infrarroja que emite el sensor y separarla en sus dos componentes. Luego modula cada componente para imitar la pulsación del tejido vivo y la devuelve al fotodetector. Al variar la amplitud y la temporización de esa modulación, el dispositivo simula distintos valores de saturación, frecuencia cardíaca y perfusión [3]. El OX-1 tiene cinco modos fijos: 85 % / 80 lpm, 95 % / 40 lpm, 98 % / 80 lpm, 98 % / 140 lpm y 99 % low perfusion. Los cuatro primeros tienen un PI aproximado de 2,0, y el último corresponde a baja perfusión, con PI ≈ 0,2 [2].

En esta práctica se evaluó técnica y funcionalmente el monitor Mindray uMEC 100 usando el simulador Pronk OxSim OX-1. Se simularon condiciones de bradicardia, hipoxemia, SpO₂ elevada con baja perfusión y taquicardia. Con ellas se calcularon los errores de medición de FC y SpO₂, se verificó la activación de alarmas frente a los límites configurados y se observó el comportamiento de la onda fotopletismográfica.

# **Metodología**

La práctica se desarrolló en tres partes. En la Parte A se revisó la información técnica de los equipos. En la Parte B se hicieron las pruebas experimentales. La Parte C correspondió al análisis y la documentación de los resultados.

## *PARTE A: Revisión técnica*

Se consulto el manual de operación del monitor Mindray uMEC 100 [1] y la información técnica del simulador Pronk OxSim OX-1 [2], [3], además de literatura sobre pulsioximetría [4]–[6] y las normas aplicables [7], [8]. Con esta revisión se identificó el modo de operación del monitor y los parámetros que simula el OX-1. También se establecieron los errores máximos permitidos (EMP) declarados por el fabricante para el módulo de SpO₂ del uMEC 100: ±2 % absoluto en SpO₂ en el rango de 70 % a 100 % (modo adulto/pediátrico) y ±3 bpm en la frecuencia de pulso [1].

## *PARTE B: Pruebas con el simulador*

1. Preparación de los registros: Se construyó una tabla para poder calcular los errores de medición de FC y SpO₂.
2. Montaje: Se encendió el uMEC 100, que entra automáticamente en modo de monitorización al arrancar [1], y se verificó que estuviera en ese modo. Luego se colocó la pinza de pulsioximetría del monitor en el dedo del simulador OxSim OX-1.
3. Bradicardia: Se seleccionó en el simulador el modo de 40 lpm y SpO₂ = 95 %. Cuando los valores se estabilizaron, se registraron las lecturas del monitor. Se calcularon los errores absoluto y porcentual de cada variable y se registró fotográficamente la onda fotopletismográfica.
4. Hipoxemia (alarma de SpO₂ baja): Se fijó el límite inferior de alarma de SpO₂ del monitor en 90 % y se seleccionó en el simulador el modo de 80 bpm y SpO₂ = 85 %. Pasados 5 s, se verificó si se activaba la alarma sonora o visual y se registraron las lecturas para calcular los errores.
5. SpO₂  elevada con alta perfusión (alarma de SpO₂  alta): Se fijó el límite superior de alarma de SpO₂ en 97 % y se seleccionó el modo de 99 % y 80 lpm con baja perfusión (PI ≈ 0,2) [2]. Pasados 5 s, se verificó la activación de la alarma, se calcularon los errores y se comparó la morfología y la amplitud de la onda con las de las condiciones anteriores.
6. Taquicardia (alarma de FC alta): Se seleccionó el modo de 140 lpm y SpO₂ = 98 %, con el límite superior de alarma de FC del monitor en **[___ lpm]**. Se registró la onda fotopletismográfica, se verificó si se activaba la alarma de frecuencia elevada y se calcularon los errores.

En cada condición, los errores se calcularon de la siguiente manera:

<img width="449" height="168" alt="image" src= https://github.com/estmarianaleyton-cmyk/Laboratorio-5./blob/main/Screenshot_20261102-143623.png>

donde X_simulado es el valor nominal del modo seleccionado en el OxSim OX-1, tomado como referencia, y X_monitor es el valor que muestra el uMEC 100. Cuando se tomó más de una lectura, se usó su promedio. Los errores se compararon con los EMP del fabricante [1]. Cada prueba de alarma se clasificó como correcta, falso positivo o falso negativo, según si el monitor respondió como se esperaba frente al límite configurado.

Es importante tener en cuenta que, según el fabricante, la exactitud de SpO₂ del uMEC 100 se validó en humanos comparando sus lecturas con muestras de sangre arterial analizadas en un CO-oxímetro. Un simulador puede usarse para verificar la exactitud de la frecuencia de pulso, pero no la de SpO₂ [1]. Por eso, en esta práctica la comparación de SpO₂ se interpreta como una verificación de la consistencia entre el valor simulado y el valor mostrado, y no como una evaluación de la exactitud clínica del oxímetro.



# **Resultados**

Durante el desarrollo de la práctica se realizaron dos series de pruebas utilizando el simulador Pronk OxSim OX-1 y el monitor Mindray uMEC 100.

Se evaluó el comportamiento del monitor frente a diferentes condiciones de frecuencia cardíaca (FC) y saturación periférica de oxígeno (SpO₂), con el propósito de verificar la precisión de las mediciones, la representación de las ondas fotopletismográficas y la activación de las alarmas.

Las condiciones evaluadas fueron:

- Bradicardia: 40 lpm y SpO₂ de 95 %.
- Hipoxemia: 80 lpm y SpO₂ de 85 %.
- Saturación elevada en modo de baja perfusión: SpO₂ de 99 %.
- Taquicardia: 140 lpm y SpO₂ de 98 %.

## Resultados de la Prueba 1

**Tabla 1. Comparación entre los valores simulados y registrados por el monitor.**

| Condición | Variable | Valor simulado | Valor medido | Error absoluto | Error porcentual |
|---|---|---:|---:|---:|---:|
| Bradicardia | FC (lpm) | 40 | 40 | 0 | 0 % |
| Bradicardia | SpO₂ (%) | 95 | 95 | 0 | 0 % |
| Hipoxemia | FC (lpm) | 80 | 80 | 0 | 0 % |
| Hipoxemia | SpO₂ (%) | 85 | 85 | 0 | 0 % |
| Baja perfusión | SpO₂ (%) | 99* | 100 | 1* | 1,01 %* |
| Taquicardia | FC (lpm) | 140 | 140 | 0 | 0 % |
| Taquicardia | SpO₂ (%) | 98 | 98 | 0 | 0 % |


Durante la primera prueba, las mediciones de frecuencia cardíaca coincidieron con los valores configurados en el simulador para las condiciones de bradicardia, hipoxemia y taquicardia.

En las mediciones de saturación de oxígeno se obtuvo una coincidencia entre los valores simulados y medidos en las condiciones de bradicardia, hipoxemia y taquicardia.

Durante la condición de baja perfusión se observó una lectura de SpO₂ de 100 %, frente al valor de referencia de 99 % establecido en la guía.

Las ondas fotopletismográficas mostraron variaciones en su periodicidad de acuerdo con la frecuencia cardíaca simulada.

## Resultados de la Prueba 2

**Tabla 2. Comparación entre los valores simulados y registrados durante la segunda prueba.**

| Condición | Variable | Valor simulado | Valor medido | Error absoluto | Error porcentual |
|---|---|---:|---:|---:|---:|
| Bradicardia | FC (lpm) | 40 | 40 | 0 | 0 % |
| Bradicardia | SpO₂ (%) | 95 | 95 | 0 | 0 % |
| Hipoxemia | FC (lpm) | 80 | 80 | 0 | 0 % |
| Hipoxemia | SpO₂ (%) | 85 | 85 | 0 | 0 % |
| Baja perfusión | SpO₂ (%) | 99 | (--) | No calculable | No calculable |
| Taquicardia | FC (lpm) | 140 | 140 | 0 | 0 % |
| Taquicardia | SpO₂ (%) | 98 | 98 | 0 | 0 % |

En la segunda prueba se obtuvieron nuevamente valores coincidentes para las condiciones de bradicardia, hipoxemia y taquicardia.

Sin embargo, durante la condición de baja perfusión, el monitor no presentó un valor numérico de saturación de oxígeno.

En la pantalla se observaron las siguientes alarmas:

- **Sin pulso.**
- **Exceso de luz para SpO₂.**

Se observó una señal fotopletismográfica periódica.

## Resultados de la verificación de alarmas

**Tabla 3. Verificación funcional del sistema de alarmas.**

| Condición | Límite configurado | Valor simulado | Alarma visual | Alarma sonora | Resultado |
|---|---|---|---|---|---|
| Hipoxemia | SpO₂ inferior: 90 % | 85 % | Sí | Sí | Correcta |
| Saturación elevada | SpO₂ superior: 97 % | 99 % | Sí | Sí | Respuesta de alarma observada |
| Taquicardia | Límite de FC no documentado | 140 lpm | Sí | Sí | Respuesta de alarma observada |
| Baja perfusión, Prueba 2 | SpO₂ superior: 97 % | 99 % | Sí | Sí | Alarma técnica correcta |

Durante las pruebas se comprobó la activación de las alarmas visuales y sonoras del monitor.

En la simulación de hipoxemia, el valor de SpO₂ de 85 % se encontraba por debajo del límite inferior configurado de 90 %, por lo que la activación de la alarma fue correcta.

En la condición de baja perfusión de la segunda prueba, el monitor generó las alarmas técnicas «Sin pulso» y «Exceso de luz para SpO₂».

# **Análisis de resultados**

## Cálculo de errores de medición

Para evaluar el desempeño del monitor se compararon los valores configurados en el simulador Pronk OxSim OX-1 con las mediciones registradas por el Mindray uMEC 100.

En cada condición se calcularon los errores absoluto y porcentual mediante las siguientes expresiones:

**Error absoluto:**

Abs = |X_monitor - X_simulado|

**Error porcentual:**

Error porcentual = (Abs / X_simulado) × 100

Donde:

- **Abs:** error absoluto.
- **X_monitor:** valor registrado por el monitor uMEC 100.
- **X_simulado:** valor nominal configurado en el simulador OxSim OX-1.

Cuando se dispone de más de una lectura para una misma condición, puede calcularse su promedio antes de determinar el error.

Los errores obtenidos deben compararse con los errores máximos permitidos (EMP) establecidos por el fabricante para cada variable.

### Ejemplo de cálculo para frecuencia cardíaca

Para una frecuencia cardíaca simulada de 40 lpm y una lectura de 40 lpm:

**Error absoluto:**

Abs = |40 - 40| = 0 lpm

**Error porcentual:**

Error porcentual = (0 / 40) × 100 = 0 %

### Ejemplo de cálculo para saturación de oxígeno

Para la condición de baja perfusión de la Prueba 1, considerando provisionalmente una SpO₂ simulada de 99 % y una lectura de 100 %:

**Error absoluto:**

Abs = |100 - 99| = 1 punto porcentual

**Error porcentual:**

Error porcentual = (1 / 99) × 100 = 1,01 %

Este resultado representa una diferencia de un punto porcentual entre el valor de referencia y la medición.

## Análisis estadístico de la frecuencia cardíaca

Durante las dos pruebas se evaluaron frecuencias cardíacas de 40, 80 y 140 lpm.

En las seis comparaciones realizadas, los valores registrados por el monitor coincidieron con los configurados en el simulador.

El error absoluto medio se calculó como:

Error absoluto medio = (0 + 0 + 0 + 0 + 0 + 0) / 6

**Error absoluto medio = 0 lpm**

El error porcentual medio fue:

**Error porcentual medio = 0 %**

Estos resultados evidencian una adecuada correspondencia entre los valores simulados y medidos.


## Análisis estadístico de la saturación periférica de oxígeno

Durante las pruebas de bradicardia, hipoxemia y taquicardia se registraron seis comparaciones válidas de SpO₂.

En estas condiciones, los valores medidos coincidieron con los simulados, obteniéndose un error absoluto de cero puntos porcentuales.

Durante la primera prueba de baja perfusión se observó una diferencia potencial de un punto porcentual.

Si se incorpora provisionalmente esta medición, el error absoluto medio se calcula como:

Error absoluto medio = (0 + 0 + 0 + 0 + 0 + 0 + 1) / 7

**Error absoluto medio = 0,14 puntos porcentuales**

El error porcentual medio se obtiene mediante:

Error porcentual medio = (0 + 0 + 0 + 0 + 0 + 0 + 1,01) / 7

**Error porcentual medio = 0,14 %**

Los resultados muestran diferencias reducidas entre los valores simulados y medidos en las condiciones evaluadas.


## Análisis de las ondas fotopletismográficas

La señal fotopletismográfica representa las variaciones del volumen sanguíneo periférico relacionadas con los ciclos cardíacos.

La frecuencia cardíaca determina la periodicidad de la señal.

El período de la onda se calcula mediante:

**T = 60 / FC**

Donde:

- **T:** período entre pulsos, en segundos.
- **FC:** frecuencia cardíaca, en latidos por minuto.

Para una frecuencia cardíaca de 40 lpm:

T = 60 / 40 = 1,50 s

Para una frecuencia cardíaca de 80 lpm:

T = 60 / 80 = 0,75 s

Para una frecuencia cardíaca de 140 lpm:

T = 60 / 140 = 0,43 s

**Tabla 4. Relación entre frecuencia cardíaca y período de la señal.**

| Condición | Frecuencia cardíaca | Período teórico |
|---|---:|---:|
| Bradicardia | 40 lpm | 1,50 s |
| Frecuencia intermedia | 80 lpm | 0,75 s |
| Taquicardia | 140 lpm | 0,43 s |

Los resultados permiten establecer que, al aumentar la frecuencia cardíaca, disminuye el intervalo temporal entre pulsos.

Durante la condición de bradicardia se observaron pulsos más separados, mientras que durante la taquicardia se identificó una mayor cantidad de oscilaciones por unidad de tiempo.

En la segunda prueba de baja perfusión se observó una señal periódica, pero el monitor no presentó una lectura válida de SpO₂.

## Análisis del funcionamiento de las alarmas

Para evaluar las alarmas del monitor, se consideraron tres posibles resultados:

- **Alarma correcta:** el monitor genera una advertencia cuando se presenta una condición que requiere alarma.
- **Falso positivo:** el monitor genera una alarma fisiológica sin que se haya presentado la condición correspondiente.
- **Falso negativo:** el monitor no genera la alarma esperada ante una condición que supera los límites configurados.

Durante la simulación de hipoxemia, la saturación de 85 % se encontraba por debajo del límite inferior de 90 %, por lo que la activación de la alarma fue correcta.

Durante la prueba de saturación elevada se observaron respuestas de alarma. 
En la condición de taquicardia se observó la activación de alarmas visuales y sonoras.

En la segunda prueba de baja perfusión, el monitor activó las alarmas técnicas «Sin pulso» y «Exceso de luz para SpO₂».

Los resultados evidencian que el sistema de alarmas respondió funcionalmente durante las condiciones evaluadas.

# **Discusión**

## ¿Cuál es el principio de operación del Pronk OxSim OX-1 para simular una onda pulsátil?

El simulador Pronk OxSim OX-1 permite reproducir condiciones controladas de pulsioximetría mediante señales que representan las variaciones ópticas asociadas con el flujo sanguíneo pulsátil.

La pulsioximetría se basa en las diferencias de absorción de luz roja e infrarroja entre la hemoglobina oxigenada y desoxigenada.

A partir de la relación entre las componentes pulsátiles de ambas señales, el monitor estima la saturación periférica de oxígeno.

Por otra parte la frecuencia del pulso se determina mediante la periodicidad de las variaciones detectadas.

Durante la práctica el simulador permitió representar frecuencias cardíacas de 40, 80 y 140 lpm, las cuales fueron identificadas correctamente por el monitor en ambas pruebas.

Este comportamiento evidencia que el sistema fue capaz de reconocer las variaciones temporales de las señales simuladas y reproducir sus valores numéricos en las condiciones evaluadas.

## ¿Por qué la SpO₂ baja puede ser un falso positivo en una situación de mala perfusión?

La baja perfusión periférica puede afectar la precisión de la pulsioximetría debido a la disminución del flujo sanguíneo pulsátil en el lugar donde se encuentra ubicado el sensor.

Cuando la amplitud de la señal disminuye, la relación señal-ruido puede deteriorarse, dificultando la identificación de las variaciones de absorción producidas por la sangre arterial.

Como consecuencia el monitor puede presentar lecturas inestables, valores inferiores a los reales o ausencia de medición.

En determinadas condiciones una lectura incorrectamente baja puede provocar una falsa alarma de hipoxemia.

Durante la segunda prueba de baja perfusión, el monitor uMEC 100 no presentó un valor numérico de SpO₂ y activó las alarmas «Sin pulso» y «Exceso de luz para SpO₂». Aunque se observó una señal fotopletismográfica periódica


## Relación entre la forma de onda, la frecuencia cardíaca y la saturación de oxígeno

La señal fotopletismográfica permite observar las variaciones del volumen sanguíneo periférico relacionadas con cada ciclo cardíaco.

Durante la condición de bradicardia de 40 lpm, los pulsos se presentan con una menor frecuencia y una mayor separación temporal.

En la condición de taquicardia de 140 lpm, los pulsos aparecen más próximos entre sí, debido al aumento de la frecuencia cardíaca.

Este comportamiento concuerda con la relación inversa entre el período de la señal y la frecuencia del pulso.

Por otra parte la saturación periférica de oxígeno no depende directamente de la frecuencia cardíaca, sino de las características de absorción óptica de la hemoglobina.

Esto explica que durante la simulación de taquicardia se registrara una frecuencia de 140 lpm con una SpO₂ del 98 %, sin que el aumento de la frecuencia implicara necesariamente una disminución de la saturación.

## Confiabilidad del monitor y limitaciones del simulador

Los resultados experimentales evidenciaron un comportamiento satisfactorio del monitor Mindray uMEC 100, tanto en la medición de los parámetros fisiológicos como en la activación de sus sistemas de alarma.

La coincidencia entre los valores simulados y medidos de frecuencia cardíaca y saturación periférica de oxígeno permitió verificar el funcionamiento del sistema de monitoreo en las condiciones evaluadas.

Adicionalmente la activación de las alarmas visuales y sonoras demostró la capacidad del equipo para advertir condiciones que superaban los límites configurados o que dificultaban la medición.

Durante la segunda prueba de baja perfusión, aunque no se obtuvo una lectura numérica de SpO₂, el monitor generó advertencias técnicas que permitieron identificar una condición de medición no válida.

Este comportamiento evidencia que la confiabilidad de un monitor no depende únicamente de la precisión de sus lecturas, sino también de su capacidad para detectar condiciones que afectan la adquisición de señales.

Por otra parte el simulador OxSim OX-1 reproduce condiciones controladas que no necesariamente representan todos los factores presentes durante una medición clínica real, como el movimiento del paciente, las variaciones de perfusión, las interferencias ópticas y las características individuales de los tejidos.

# **Conclusiones**





# **Referencias**
[1] Shenzhen Mindray Bio-Medical Electronics Co., Ltd., uMEC 60/uMEC 70/uMEC 80/uMEC 100/uMEC 120/uMEC 150 Patient Monitor – Operator's Manual, rev. 2.0, P/N 046-026551-00. Shenzhen, China, 2023.

[2] Pronk Technologies Inc., "OX-1 OxSim," MedWrench. [En línea]. Disponible en: https://www.medwrench.com/equipment/3862/pronk-technologies-ox-1-oxsim

[3] K. A. Ruiter, "Light transmission simulator for pulse oximeter," U.S. Patent 7 346 378 B2, 18 mar. 2008 (cesionario: Pronk Technologies Inc.).

[4] E. D. Chan, M. M. Chan y M. M. Chan, "Pulse oximetry: Understanding its basic principles facilitates appreciation of its limitations," Respiratory Medicine, vol. 107, n.º 6, pp. 789–799, 2013, doi: 10.1016/j.rmed.2013.02.004.

[5] A. Jubran, "Pulse oximetry," Critical Care, vol. 19, art. 272, 2015, doi: 10.1186/s13054-015-0984-8.

[6] J. Allen, "Photoplethysmography and its application in clinical physiological measurement," Physiological Measurement, vol. 28, n.º 3, pp. R1–R39, 2007, doi: 10.1088/0967-3334/28/3/R01.

[7] Medical electrical equipment – Part 2-61: Particular requirements for basic safety and essential performance of pulse oximeter equipment, ISO 80601-2-61:2017.

[8] Medical electrical equipment – Part 1-8: General requirements for basic safety and essential performance – Collateral standard: General requirements, tests and guidance for alarm systems in medical electrical equipment and medical electrical systems, IEC 60601-1-8:2006+AMD1:2012+AMD2:2020.

[9] J. G. Webster, Ed., Medical Instrumentation: Application and Design, 4.ª ed. Hoboken, NJ, EE. UU.: Wiley, 2010.
