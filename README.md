# Diseño-Fuente-de-Alimentación

# Electronica

Creación de una fuente de alimentación variable entre 5-12 V con entrada de 230V 50Hz
Se tiene como objetivo de este proyecto la explicación de las diversas estapas de las que se construye una FA, las cuales son denominadas transformación, rectificación, filtrado y regulación

Como componentes utilizados encontramos los siguientes:
1. Transformador de 230V a 12V
2. 4 Diodos 1N4007 para el puente rectificador de onda completa
3. Condensador de filtrado electrolítico de 2200uF y 25V
4. Regulador de voltaje LM7805 para fijar la salida a 5V
5. Potenciometro de 1k ohm para ajustar la tensión de salida
6. Resistencia de 1000 ohm
7. Resistencia de 470 ohm
8. LED indicador

El proyecto se compone de 4 etapas bien definidas:
1. Transformación: El transformador reducirá la tensión de la red eléctrica (230V AC) a 12V AC
2. Rectificación: Los 4 diodos 1N4007 forman lo que se conoce como "Puente de Graetz", que convierte la se corriente alterna (AC) en una señal pulsante de corriente continua (DC)
3. Filtrado: El condensador electrolitico de 2200uF actúa como un alamcén de energía "alisando" los pulsos de la rectificación y reduciendo el rizado para obtener una línea de DC mucho más estable
4. Regulación: El circuito integrado 7805 toma la tensión filtrada y la estabiliza a una salida exacta y limpia de 5V DC, protegiendo la carga contra variaciones

Esquema Eléctronico:

