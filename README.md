# Diseño-Fuente-de-Alimentación

# Especificaciones técnicas

Creación de una fuente de alimentación variable entre 5-12 V con entrada de 230V 50Hz
Se tiene como objetivo de este proyecto la explicación de las diversas estapas de las que se construye una FA, las cuales son denominadas transformación, rectificación, filtrado y regulación

Como componentes utilizados encontramos los siguientes:
1. Transformador de 230V a 12V
2. 4 Diodos 1N4007 para el puente rectificador de onda completa
3. Condensador de filtrado electrolítico de 2200uF y 25V
4. Regulador de voltaje LM7805 para la salida a 5V
5. Potenciometro de 1k ohm para ajustar la tensión de salida
6. Resistencia de 1000 ohm
7. Resistencia de 470 ohm
8. LED indicador

El proyecto se compone de 4 etapas bien definidas:
1. Transformación: El transformador reducirá la tensión de la red eléctrica (230V AC) a 12V AC
2. Rectificación: Los 4 diodos 1N4007 forman lo que se conoce como "Puente de Graetz", que convierte la se corriente alterna (AC) en una señal pulsante de corriente continua (DC)
3. Filtrado: El condensador electrolitico de 2200uF actúa como un alamcén de energía "alisando" los pulsos de la rectificación y reduciendo el rizado para obtener una línea de DC mucho más estable
4. Regulación: El circuito integrado 7805 toma la tensión filtrada y la estabiliza a una salida exacta y limpia de 5V DC, protegiendo la carga contra variaciones

## Justificación de cálculos y diseño de la FA

Para justificar el diseño de la fuente de alimentación, se han aplicado las siguientes ecuaciones de la electrónica analógica:

### 1. Voltaje de Pico tras el Filtrado ($V_{max}$)
La tensión alterna del secundario del transformador ($V_{RMS} = 12\text{V}$) se rectifica en onda completa. Restando la caída de los diodos del puente ($\approx 1.4\text{V}$), la tensión continua máxima en el condensador es:

$$V_{max} = (V_{RMS} \times \sqrt{2}) - V_{diodos}$$

$$V_{max} = (12\text{V} \times 1.4142) - 1.4\text{V} \approx 15.57\text{V  DC}$$

### 2. Voltaje de Rizado ($\Delta V$)
El rizado de la señal en el condensador de $2200\mu\text{F}$ depende de la corriente de carga ($I_L$) y de la frecuencia de la señal rectificada ($f = 100\text{Hz}$):

$$\Delta V = \frac{I_L}{f \times C}$$

Si asumimos un consumo estimado de $0.5\text{A}$:
$$\Delta V = \frac{0.5\text{A}}{100\text{Hz} \times 2200 \times 10^{-6}\text{F}} \approx 2.27\text{V}$$

### 3. Tensión de Salida Variable ($V_{out}$)
El regulador LM7805 mantiene $5\text{V}$ fijos entre sus pines OUT y GND. Al elevar la tensión de su pin GND con el divisor formado por $R_2$ ($470\Omega$) y el potenciómetro $R_3$ ($1\text{k}\Omega$), la ecuación de salida es:

$$V_{out} = V_{7805} \times \left(1 + \frac{R_3}{R_2}\right) + (I_q \times R_3)$$

*Donde $I_q \approx 5\text{mA}$ es la corriente de reposo del integrado.*

* **Con el potenciómetro al mínimo ($R_3 = 0\Omega$):** $V_{out} = 5\text{V}$
* **Con el potenciómetro al máximo ($R_3 = 1000\Omega$):** $V_{out} \approx 20.63\text{V}$ *(Teórico, limitado en la práctica por la tensión de entrada a $\approx 13.5\text{V}$).*

### 4. Corriente del LED de Comprobación ($I_{LED}$)
Para el LED verde conectado a la etapa de filtrado con la resistencia $R_1 = 1000\Omega$:

$$I_{LED} = \frac{V_{max} - V_{\gamma}}{R_1}$$

$$I_{LED} = \frac{15.57\text{V} - 2\text{V}}{1000\Omega} \approx 13.57\text{mA}$$
$$

Esquema Eléctronico:

<img width="546" height="221" alt="image" src="https://github.com/user-attachments/assets/a99d50dd-718e-46a5-b30d-3b661b8255f1" />


