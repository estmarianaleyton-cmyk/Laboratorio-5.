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


# Laboratorio 5. Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas

**Asignatura:** Instrumentación Biomédica y Biosensores  
**Universidad:** Universidad Militar Nueva Granada  
**Equipos:** Simulador Pronk OxSim OX-1 y monitor Mindray uMEC 100.

---

# 1. Resultados

Durante el desarrollo de la práctica se realizaron dos series de pruebas utilizando el simulador de parámetros hemodinámicos Pronk OxSim OX-1 y el monitor de signos vitales Mindray uMEC 100.

El objetivo fue evaluar el comportamiento del monitor frente a diferentes condiciones simuladas de frecuencia cardíaca (FC) y saturación periférica de oxígeno (SpO₂), verificando la precisión de las mediciones, la representación de las ondas fotopletismográficas y la activación de alarmas.

Se evaluaron cuatro condiciones:

- Bradicardia.
- Hipoxemia.
- Saturación elevada en modo de baja perfusión (*Low Perfusion*).
- Taquicardia.

## 1.1. Resultados de la Prueba 1

**Tabla 1. Comparación de los valores simulados y medidos durante la Prueba 1.**

| Condición | Variable | Valor simulado | Valor medido | Error absoluto | Error porcentual |
|---|---|---:|---:|---:|---:|
| Bradicardia | FC (lpm) | 40 | 40 | 0 | 0 % |
| Bradicardia | SpO₂ (%) | 95 | 95 | 0 | 0 % |
| Hipoxemia | FC (lpm) | 80 | 80 | 0 | 0 % |
| Hipoxemia | SpO₂ (%) | 85 | 85 | 0 | 0 % |
| Baja perfusión | SpO₂ (%) | 99* | 100 | 1* | 1,01 %* |
| Taquicardia | FC (lpm) | 140 | 140 | 0 | 0 % |
| Taquicardia | SpO₂ (%) | 98 | 98 | 0 | 0 % |

*El valor de referencia de 99 % corresponde al procedimiento indicado en la guía. El error de baja perfusión es provisional hasta confirmar que ese fue el valor configurado en el simulador.*

En la primera prueba se observó una correspondencia entre los valores de frecuencia cardíaca simulados y los registrados por el monitor. Para las condiciones de 40, 80 y 140 lpm se obtuvo un error absoluto de 0 lpm.

En cuanto a la saturación de oxígeno, las condiciones de bradicardia, hipoxemia y taquicardia presentaron coincidencia entre los valores simulados y medidos.

Durante la condición de baja perfusión se observó una lectura de 100 %, frente al valor de referencia de 99 % establecido en el procedimiento.

Las fotografías también permitieron identificar cambios en la periodicidad de las ondas fotopletismográficas, especialmente al comparar las condiciones de bradicardia y taquicardia.

## 1.2. Resultados de la Prueba 2

**Tabla 2. Comparación de los valores simulados y medidos durante la Prueba 2.**

| Condición | Variable | Valor simulado | Valor medido | Error absoluto | Error porcentual |
|---|---|---:|---:|---:|---:|
| Bradicardia | FC (lpm) | 40 | 40 | 0 | 0 % |
| Bradicardia | SpO₂ (%) | 95 | 95 | 0 | 0 % |
| Hipoxemia | FC (lpm) | 80 | 80 | 0 | 0 % |
| Hipoxemia | SpO₂ (%) | 85 | 85 | 0 | 0 % |
| Baja perfusión | SpO₂ (%) | 99 | Sin lectura (--) | No calculable | No calculable |
| Taquicardia | FC (lpm) | 140 | 140 | 0 | 0 % |
| Taquicardia | SpO₂ (%) | 98 | 98 | 0 | 0 % |

En la segunda prueba se obtuvieron nuevamente mediciones coincidentes para las condiciones de bradicardia, hipoxemia y taquicardia.

Sin embargo, durante la simulación en modo *Low Perfusion*, el monitor no presentó un valor numérico de saturación periférica de oxígeno.

En la pantalla se observaron guiones en lugar de la lectura de SpO₂ y se identificaron las alarmas:

- **Sin pulso.**
- **Exceso de luz para SpO₂.**

A pesar de la ausencia de una medición numérica válida, se observó una onda fotopletismográfica periódica en la pantalla del equipo.

Este resultado representa una diferencia importante respecto a la primera prueba, ya que evidencia una condición en la cual el monitor no logró proporcionar una lectura válida de saturación.

## 1.3. Verificación de alarmas

**Tabla 3. Condiciones de alarma evaluadas durante la práctica.**

| Condición | Límite configurado | Valor simulado | Evidencia observada |
|---|---|---|---|
| Hipoxemia | SpO₂ inferior: 90 % | SpO₂: 85 % | Aviso visual de alarma |
| Saturación elevada | SpO₂ superior: 97 % | SpO₂: 99 % | Avisos visuales; en Prueba 2 no hubo lectura válida |
| Taquicardia | Límite superior de FC no documentado | FC: 140 lpm | Aviso visual en las capturas |
| Baja perfusión – Prueba 2 | SpO₂ superior: 97 % | SpO₂: 99 % | Alarmas «Sin pulso» y «Exceso de luz para SpO₂» |

Durante las pruebas se identificaron avisos visuales asociados con las condiciones simuladas.

No obstante, las fotografías no permiten determinar con precisión los tiempos de activación ni verificar las alarmas sonoras.

Por lo tanto, la evaluación de alarmas se considera parcial, debido a que no se dispone de un registro temporal que permita comprobar el cumplimiento de los cinco segundos establecidos en la guía.

---

# 2. Análisis de resultados

## 2.1. Cálculo de errores de medición

Para evaluar la precisión de las mediciones se calcularon los errores absolutos y porcentuales entre los valores configurados en el simulador Pronk OxSim OX-1 y los valores registrados por el monitor Mindray uMEC 100.

El error absoluto se determinó mediante:

$$
E_a = |X_m-X_s|
$$

Donde:

- \(E_a\): error absoluto.
- \(X_m\): valor medido por el monitor.
- \(X_s\): valor configurado en el simulador.

El error porcentual se calculó mediante:


$$
E_{\mathrm{porcentual}} = \frac{\left|X_m-X_s\right|}{X_s}\times 100
$$


Por ejemplo, para la medición de saturación elevada de la primera prueba, considerando el valor de referencia de 99 % establecido en la guía y la lectura observada de 100 %:

$$
E_a = |100-99| = 1
$$

$$
E_{\%} = \frac{1}{99}\times100 = 1{,}01\%
$$

Este cálculo corresponde a una diferencia de un punto porcentual de SpO₂ y queda sujeto a confirmar la configuración real del simulador.

## 2.2. Análisis estadístico de la frecuencia cardíaca

Durante las dos pruebas se registraron valores de frecuencia cardíaca de 40, 80 y 140 lpm, correspondientes a las condiciones de bradicardia, hipoxemia y taquicardia.

En las seis comparaciones realizadas, los valores medidos coincidieron con los configurados en el simulador.

Por lo tanto, el error absoluto medio fue:

$$
E_{a,\mathrm{medio}} = \frac{0+0+0+0+0+0}{6}
$$

$$
E_{a,\mathrm{medio}} = 0\ \mathrm{lpm}
$$

El error porcentual medio también fue del 0 %.

Estos resultados indican que el monitor presentó una correspondencia exacta con los valores simulados, considerando la resolución de lectura utilizada.

Sin embargo, debido a que se dispone de un número reducido de mediciones y únicamente se evaluaron tres valores de frecuencia cardíaca, no es posible garantizar la exactitud del equipo en todo su intervalo de operación.

## 2.3. Análisis estadístico de la saturación periférica de oxígeno

En las condiciones de bradicardia, hipoxemia y taquicardia se registraron seis comparaciones válidas de SpO₂, todas con un error absoluto de cero puntos porcentuales.

En la primera prueba de baja perfusión se observó una diferencia potencial de un punto porcentual respecto al valor indicado en la guía.

Si se incluye provisionalmente esta medición, el error absoluto medio es:

$$
E_{a,\mathrm{medio}} = \frac{0+0+0+0+0+0+1}{7}
$$

$$
E_{a,\mathrm{medio}} \approx 0{,}14
$$

El error porcentual medio correspondiente es aproximadamente:

$$
E_{\%,\mathrm{medio}} = \frac{1{,}01}{7}
$$

$$
E_{\%,\mathrm{medio}} \approx 0{,}14\%
$$

Estos valores reflejan diferencias reducidas entre las mediciones disponibles.

Sin embargo, en la segunda prueba de baja perfusión no se obtuvo una lectura válida de SpO₂, por lo que este resultado no se incluyó en los cálculos estadísticos.

La ausencia de lectura constituye un resultado funcional relevante, debido a que evidencia una limitación del sistema para proporcionar información numérica bajo determinadas condiciones de señal.

## 2.4. Relación entre la onda fotopletismográfica y la frecuencia cardíaca

La señal fotopletismográfica representa las variaciones del volumen sanguíneo periférico asociadas con los ciclos cardíacos.

La relación entre el período de la señal y la frecuencia cardíaca se expresa mediante:

$$
T = \frac{60}{FC}
$$

Para la condición de bradicardia de 40 lpm:

$$
T = \frac{60}{40} = 1{,}5\ \mathrm{s}
$$

Para una frecuencia de 80 lpm:

$$
T = \frac{60}{80} = 0{,}75\ \mathrm{s}
$$

Para la condición de taquicardia de 140 lpm:

$$
T = \frac{60}{140} \approx 0{,}43\ \mathrm{s}
$$

Estos resultados teóricos permiten explicar las diferencias observadas entre las ondas registradas en las fotografías.

En bradicardia, los pulsos presentan una mayor separación temporal, mientras que en taquicardia se observa una mayor cantidad de pulsos por unidad de tiempo.

En la segunda prueba de baja perfusión se observó una onda periódica, pero el monitor no proporcionó una lectura válida de SpO₂.

Esto indica que la presencia de una señal visual no garantiza necesariamente que el equipo pueda calcular un valor confiable de saturación.

## 2.5. Análisis del funcionamiento de las alarmas

Las alarmas constituyen un mecanismo de seguridad fundamental en los monitores de signos vitales, debido a que permiten advertir condiciones fisiológicas que superan los límites establecidos.

Durante la simulación de hipoxemia, el valor de SpO₂ de 85 % se encontraba por debajo del límite inferior configurado de 90 %, condición que debería generar una alarma.

En la prueba de saturación elevada, el valor de referencia de 99 % superaba el límite superior de 97 %.

Sin embargo, durante la segunda prueba de baja perfusión, el monitor presentó las alarmas «Sin pulso» y «Exceso de luz para SpO₂», junto con la ausencia de una lectura numérica válida.

Este comportamiento demuestra la importancia de diferenciar las alarmas fisiológicas, asociadas con valores fuera de los límites establecidos, de las alarmas técnicas relacionadas con dificultades en la adquisición o procesamiento de la señal.

Aunque se observaron avisos visuales, no fue posible verificar experimentalmente los tiempos de respuesta de las alarmas ni su componente sonoro.

---

# 3. Discusión

## 3.1. ¿Cuál es el principio de operación del Pronk OxSim OX-1 para simular una onda pulsátil?

El simulador Pronk OxSim OX-1 permite reproducir condiciones controladas de pulsioximetría mediante señales que representan las variaciones ópticas asociadas con el flujo sanguíneo pulsátil.

La pulsioximetría se fundamenta en las diferencias de absorción de luz roja e infrarroja entre la hemoglobina oxigenada y desoxigenada.

A partir de la relación entre las componentes pulsátiles de ambas señales, el monitor estima la saturación periférica de oxígeno.

Por otra parte, la frecuencia del pulso se determina mediante la periodicidad de las variaciones detectadas.

Durante la práctica, el simulador permitió representar frecuencias cardíacas de 40, 80 y 140 lpm, las cuales fueron identificadas correctamente por el monitor en ambas pruebas.

Este comportamiento demuestra que el sistema fue capaz de reconocer las variaciones temporales de las señales simuladas y reproducir sus valores numéricos en las condiciones evaluadas.

## 3.2. ¿Por qué la SpO₂ baja puede ser un falso positivo en una situación de mala perfusión?

La baja perfusión periférica puede afectar la precisión de la pulsioximetría debido a la disminución del flujo sanguíneo pulsátil en el lugar donde se encuentra ubicado el sensor.

Cuando la amplitud de la señal disminuye, la relación señal-ruido puede deteriorarse, dificultando la identificación de las variaciones de absorción producidas por la sangre arterial.

Como consecuencia, el monitor puede presentar lecturas inestables, valores inferiores a los reales o ausencia de medición.

En determinadas condiciones, una lectura incorrectamente baja puede provocar una falsa alarma de hipoxemia.

Durante la segunda prueba de baja perfusión, el monitor uMEC 100 no presentó un valor numérico de SpO₂ y activó las alarmas:

- **Sin pulso.**
- **Exceso de luz para SpO₂.**

Aunque se observó una señal fotopletismográfica periódica, el equipo no logró mostrar una medición válida.

Este comportamiento podría estar relacionado con dificultades en la detección de la señal pulsátil o con interferencias ópticas.

Sin embargo, la fotografía no permite determinar de manera concluyente cuál fue la causa.

Es importante señalar que este resultado no corresponde a una falsa lectura baja de SpO₂, sino a una ausencia de lectura acompañada de alarmas técnicas.

Por lo tanto, la prueba evidencia la importancia de considerar la calidad de la señal antes de interpretar una medición de saturación o una alarma de hipoxemia.

## 3.3. Relación entre la forma de onda, la frecuencia cardíaca y la saturación de oxígeno

La señal fotopletismográfica permite observar las variaciones del volumen sanguíneo periférico relacionadas con cada ciclo cardíaco.

Durante la condición de bradicardia de 40 lpm, los pulsos se presentan con una menor frecuencia y una mayor separación temporal.

En la condición de taquicardia de 140 lpm, los pulsos aparecen más próximos entre sí, debido al aumento de la frecuencia cardíaca.

Este comportamiento concuerda con la relación inversa entre el período de la señal y la frecuencia del pulso.

Por otra parte, la saturación periférica de oxígeno no depende directamente de la frecuencia cardíaca, sino de las características de absorción óptica de la hemoglobina.

Esto explica que durante la simulación de taquicardia se registrara una frecuencia de 140 lpm con una SpO₂ del 98 %, sin que el aumento de la frecuencia implicara necesariamente una disminución de la saturación.

## 3.4. Confiabilidad del monitor y limitaciones del simulador

Los resultados experimentales muestran que el monitor Mindray uMEC 100 presentó una buena correspondencia con los valores configurados en el simulador Pronk OxSim OX-1, especialmente en las mediciones de frecuencia cardíaca.

Sin embargo, durante la segunda prueba de baja perfusión se presentó una condición en la que el monitor no logró proporcionar una lectura válida de saturación.

Este resultado evidencia que el desempeño del sistema no depende únicamente de la configuración de los parámetros simulados, sino también de la calidad de la señal recibida y de las condiciones de funcionamiento del sensor.

Además, el simulador reproduce condiciones controladas que no necesariamente representan todos los factores presentes durante una medición clínica real, como el movimiento del paciente, las variaciones de perfusión, las interferencias ópticas y las características individuales de los tejidos.

Por lo tanto, aunque las pruebas permitieron verificar el funcionamiento básico del monitor, los resultados no son suficientes para garantizar su confiabilidad clínica en todas las condiciones de uso.

---

# 4. Conclusiones

1. Se realizó la evaluación funcional del monitor de signos vitales Mindray uMEC 100 mediante el simulador Pronk OxSim OX-1, reproduciendo condiciones de bradicardia, hipoxemia, baja perfusión y taquicardia. Esto permitió analizar el comportamiento del equipo frente a diferentes valores de frecuencia cardíaca y saturación periférica de oxígeno.

2. Las mediciones de frecuencia cardíaca presentaron un error absoluto de 0 lpm y un error porcentual del 0 % en las seis comparaciones realizadas. Estos resultados evidencian una adecuada correspondencia entre los valores simulados y medidos en los puntos evaluados.

3. Las mediciones válidas de saturación periférica de oxígeno presentaron una buena correspondencia con los valores configurados. En la primera prueba de baja perfusión se identificó una diferencia potencial de un punto porcentual respecto al valor establecido en la guía, mientras que en la segunda prueba no se obtuvo una lectura numérica válida.

4. Durante la segunda prueba en modo *Low Perfusion* se observaron las alarmas «Sin pulso» y «Exceso de luz para SpO₂», acompañadas de la ausencia de una medición numérica. Este resultado permitió identificar una limitación funcional del sistema bajo las condiciones evaluadas y resaltó la importancia de considerar la calidad de la señal durante la interpretación de los parámetros fisiológicos.

5. El análisis de las ondas fotopletismográficas permitió relacionar la frecuencia cardíaca con la separación temporal entre pulsos. Se estableció que, al aumentar la frecuencia cardíaca de 40 a 140 lpm, el período teórico disminuye de 1,5 a aproximadamente 0,43 segundos, comportamiento coherente con las señales observadas.

6. La verificación de alarmas permitió identificar respuestas visuales durante algunas condiciones simuladas. Sin embargo, no fue posible comprobar el tiempo de activación de cinco segundos ni la presencia de alarmas sonoras, debido a la ausencia de registros temporales y auditivos.

7. Se concluye que el monitor uMEC 100 presentó un desempeño consistente en las mediciones verificables, mientras que el simulador OxSim OX-1 permitió reproducir condiciones controladas útiles para la evaluación de equipos biomédicos. No obstante, para determinar de manera integral la confiabilidad del sistema es necesario complementar las pruebas con mediciones repetidas, análisis de incertidumbre y verificación de las alarmas bajo condiciones controladas.



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
