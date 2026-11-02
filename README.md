# Laboratorio-5

**Universidad Militar Nueva Granada**

**Asignatura:** Instrumentación biomedica y biosensores

**Estudiantes:** Dubrasca Martínez, Mariana Leyton, Joshara Valentina Palacios

**Fecha:** 28 de octubre del 2026

**Título de la práctica:** Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas

# **Introducción**

La monitorización continua de variables fisiológicas es una herramienta central en la atención clínica, porque permite detectar a tiempo el deterioro del paciente. Entre estas variables, la frecuencia cardíaca (FC) y la saturación periférica de oxígeno (SpO₂) están entre las más utilizadas. La FC refleja el ritmo de bombeo del corazón. La SpO₂ estima qué fracción de la hemoglobina arterial está transportando oxígeno [4], [5]. Condiciones como la bradicardia, la taquicardia o la hipoxemia pueden poner en riesgo inmediato al paciente. Por eso, los monitores de signos vitales deben medir estas variables con exactitud y, además, generar alarmas confiables cuando sus valores salen de los límites configurados. Estos requisitos están regulados por normas internacionales como la ISO 80601-2-61, para pulsioxímetros, y la IEC 60601-1-8, para sistemas de alarma en equipos electromédicos [7], [8].

La SpO₂ se mide de forma no invasiva mediante pulsioximetría. La técnica se basa en que la oxihemoglobina y la desoxihemoglobina absorben de manera diferente la luz roja (≈660 nm) y la infrarroja (≈940 nm). El sensor emite ambas longitudes de onda a través de un lecho vascular, normalmente el dedo, y un fotodetector registra la luz transmitida [4], [9]. Con cada latido, el volumen de sangre arterial aumenta y disminuye. Esto genera una componente pulsátil (AC) superpuesta a una componente constante (DC), que corresponde al tejido, la sangre venosa y la sangre arterial no pulsátil. Esa señal es la onda fotopletismográfica (PPG) que aparece en el monitor [6]. El equipo calcula el cociente de las relaciones AC/DC de ambas longitudes de onda, R = (AC_rojo/DC_rojo)/(AC_IR/DC_IR), y con una curva de calibración empírica lo convierte en un valor de SpO₂. La FC se obtiene a partir del intervalo entre pulsos consecutivos [4], [5]. Como la medición depende de una señal pulsátil adecuada, factores como la baja perfusión periférica, el movimiento o la luz ambiental pueden degradar la PPG y producir lecturas erróneas o falsas alarmas [4], [5]. Para cuantificar la calidad de la señal se usa el índice de perfusión (PI), que es la relación porcentual entre la componente pulsátil y la no pulsátil [1].

No es ético ni práctico inducir condiciones patológicas en pacientes para verificar el funcionamiento de un monitor. Por eso se usan simuladores de parámetros fisiológicos. El Pronk OxSim OX-1 es un simulador óptico de SpO₂ con un "dedo" fijo, que permite evaluar el sistema completo de pulsioximetría, incluido el sensor [2]. Su principio de funcionamiento consiste en captar la luz roja e infrarroja que emite el sensor y separarla en sus dos componentes. Luego modula cada componente para imitar la pulsación del tejido vivo y la devuelve al fotodetector. Al variar la amplitud y la temporización de esa modulación, el dispositivo simula distintos valores de saturación, frecuencia cardíaca y perfusión [3]. El OX-1 tiene cinco modos fijos: 85 % / 80 bpm, 95 % / 40 bpm, 98 % / 80 bpm, 98 % / 140 bpm y 99 % low perfusion. Los cuatro primeros tienen un PI aproximado de 2,0, y el último corresponde a baja perfusión, con PI ≈ 0,2 [2].

En esta práctica se evaluó técnica y funcionalmente el monitor Mindray uMEC 100 usando el simulador Pronk OxSim OX-1. Se simularon condiciones de bradicardia, hipoxemia, SpO₂ elevada con baja perfusión y taquicardia. Con ellas se calcularon los errores de medición de FC y SpO₂, se verificó la activación de alarmas frente a los límites configurados y se observó el comportamiento de la onda fotopletismográfica.

# **Metodología**

La práctica se desarrolló en tres partes. En la Parte A se revisó la información técnica de los equipos. En la Parte B se hicieron las pruebas experimentales. La Parte C correspondió al análisis y la documentación de los resultados.

## *PARTE A: Revisión técnica*

Se consulto el manual de operación del monitor Mindray uMEC 100 [1] y la información técnica del simulador Pronk OxSim OX-1 [2], [3], además de literatura sobre pulsioximetría [4]–[6] y las normas aplicables [7], [8]. Con esta revisión se identificó el modo de operación del monitor y los parámetros que simula el OX-1. También se establecieron los errores máximos permitidos (EMP) declarados por el fabricante para el módulo de SpO₂ del uMEC 100: ±2 % absoluto en SpO₂ en el rango de 70 % a 100 % (modo adulto/pediátrico) y ±3 bpm en la frecuencia de pulso [1].

## *PARTE B: Pruebas con el simulador*

1. Preparación de los registros: Se construyó una tabla para poder calcular los errores de medición de FC y SpO₂.
2. Montaje: Se encendió el uMEC 100, que entra automáticamente en modo de monitorización al arrancar [1], y se verificó que estuviera en ese modo. Luego se colocó la pinza de pulsioximetría del monitor en el dedo del simulador OxSim OX-1.
3. Bradicardia: Se seleccionó en el simulador el modo de 40 bpm y SpO₂ = 95 %. Cuando los valores se estabilizaron, se registraron las lecturas del monitor **[indicar cuántas]**. Se calcularon los errores absoluto y porcentual de cada variable y se registró fotográficamente la onda fotopletismográfica.
4. Hipoxemia (alarma de SpO₂ baja): Se fijó el límite inferior de alarma de SpO₂ del monitor en 90 % y se seleccionó en el simulador el modo de 80 bpm y SpO₂ = 85 %. Pasados 5 s, se verificó si se activaba la alarma sonora o visual y se registraron las lecturas para calcular los errores.
5. SpO₂  elevada con alta perfusión (alarma de SpO₂  alta): Se fijó el límite superior de alarma de SpO₂ en 97 % y se seleccionó el modo de 99 % y 80 bpm con baja perfusión (PI ≈ 0,2) [2]. Pasados 5 s, se verificó la activación de la alarma, se calcularon los errores y se comparó la morfología y la amplitud de la onda con las de las condiciones anteriores.
6. Taquicardia (alarma de FC alta): Se seleccionó el modo de 140 bpm y SpO₂ = 98 %, con el límite superior de alarma de FC del monitor en **[___ lpm]**. Se registró la onda fotopletismográfica, se verificó si se activaba la alarma de frecuencia elevada y se calcularon los errores.

En cada condición, los errores se calcularon de la siguiente manera:

<img width="449" height="168" alt="image" src= https://github.com/estmarianaleyton-cmyk/Laboratorio-5./blob/main/Screenshot_20261102-143623.png>

donde X_simulado es el valor nominal del modo seleccionado en el OxSim OX-1, tomado como referencia, y X_monitor es el valor que muestra el uMEC 100. Cuando se tomó más de una lectura, se usó su promedio. Los errores se compararon con los EMP del fabricante [1]. Cada prueba de alarma se clasificó como correcta, falso positivo o falso negativo, según si el monitor respondió como se esperaba frente al límite configurado.

Es importante tener en cuenta que, según el fabricante, la exactitud de SpO₂ del uMEC 100 se validó en humanos comparando sus lecturas con muestras de sangre arterial analizadas en un CO-oxímetro. Un simulador puede usarse para verificar la exactitud de la frecuencia de pulso, pero no la de SpO₂ [1]. Por eso, en esta práctica la comparación de SpO₂ se interpreta como una verificación de la consistencia entre el valor simulado y el valor mostrado, y no como una evaluación de la exactitud clínica del oxímetro.


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
