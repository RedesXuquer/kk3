---
title: Binario, Hexadecimal y Decimal
date: 2023-09-23 20:30:00 +0100
categories: [Sistemas Microinformáticos y Redes, Redes Locales]
tags: [redes locales, binario, decimal, hexadecimal, tsmr]
img_path: /assets/img/binario/
image: 
    path: binario.jpg
---

{:.section}
## ¿Qué es el sistema binario?

El sistema binario es un sistema numérico que utiliza solo dos dígitos para representar números y realizar operaciones matemáticas: 0 y 1. Este sistema es fundamental en la informática y la electrónica, ya que se adapta perfectamente a la forma en que los ordenadores almacenan y procesan la información en forma de corriente eléctrica (encendido/apagado) y se utiliza como base para todos los cálculos y operaciones que realizan.

A diferencia del sistema decimal, que utiliza diez dígitos (0 al 9) para representar números, el sistema binario se limita a dos dígitos, lo que lo hace muy eficiente y fácil de implementar en circuitos electrónicos. Cada dígito binario se llama un "bit" (abreviatura de "binary digit"). Los bits se agrupan en conjuntos más grandes llamados "bytes" para representar información más compleja.

El sistema binario se basa en los mismos principios que otros sistemas numéricos, como el decimal. Por ejemplo, en el sistema decimal, el valor de cada posición en un número se multiplica por diez a la potencia de la posición. En el sistema binario, el valor de cada posición se multiplica por dos a la potencia de la posición. Por lo tanto, un número binario se puede expresar como una suma de potencias de dos.

Por ejemplo, consideremos el número binario "1011", que consta de cuatro bits. Podemos calcular su valor en base 10 de la siguiente manera:

- El bit más a la derecha tiene un valor de 2^0 = 1.
- El siguiente bit tiene un valor de 2^1 = 2.
- El siguiente bit tiene un valor de 2^2 = 4.
- El bit más a la izquierda tiene un valor de 2^3 = 8.
- Entonces, el número binario "1011" en base 10 es igual a 8 + 0 + 2 + 1 = 11.

El sistema binario es esencial en la programación de computadoras porque todas las operaciones de la CPU se realizan en binario. Los programas y datos se almacenan en memoria en formato binario, y los circuitos electrónicos dentro de las computadoras utilizan señales binarias para representar y procesar información. Además, el sistema binario se utiliza para representar información en forma de texto, gráficos, audio y video en las computadoras.

En resumen, el sistema binario es un sistema numérico que utiliza solo dos dígitos, 0 y 1, para representar números y es fundamental en la informática y la electrónica debido a su eficiencia y capacidad para representar y procesar información en el mundo de las computadoras y la tecnología digital.

{:.section}
## Pasar de binario a decimal

Para convertir un número binario a decimal, simplemente debes entender cómo funcionan las posiciones en el sistema binario y cómo calcular el valor decimal correspondiente. Aquí tienes un paso a paso para realizar esta conversión:

1. Escribe el número binario que deseas convertir. Por ejemplo, tomemos el número binario "101101".

2. Enumera las posiciones de derecha a izquierda, comenzando desde 0 y aumentando en 1 para cada posición hacia la izquierda. Esto se llama "posición de bits" y se usa para asignar poderes de 2 a cada dígito binario. Por ejemplo:

| 5 | 4 | 3 | 2 | 1 | 0 |
| 1 | 0 | 1 | 1 | 0 | 1 |

3. Ahora, para convertir el número binario a decimal, realiza los siguientes pasos para cada dígito binario:
- Multiplica el dígito binario (0 o 1) por 2 elevado a la potencia de su posición de bits.
- Suma estos valores para obtener el equivalente decimal.
- Siguiendo nuestro ejemplo:

- Para el bit en la posición 0: 1 * 2^0 = 1.
- Para el bit en la posición 1: 0 * 2^1 = 0.
- Para el bit en la posición 2: 1 * 2^2 = 4.
- Para el bit en la posición 3: 1 * 2^3 = 8.
- Para el bit en la posición 4: 0 * 2^4 = 0.
- Para el bit en la posición 5: 1 * 2^5 = 32.

4. Ahora, suma todos estos valores juntos:

1 + 4 + 8 + 0 + 32 = 45

Entonces, el número binario "101101" es igual a 45 en decimal.

En resumen, para convertir un número binario a decimal, debes multiplicar cada dígito binario por 2 elevado a la potencia de su posición de bits correspondiente y luego sumar estos valores. Esto te dará el valor decimal equivalente.

{:.subsection}
### Consejos para el paso de binario a decimal
- Si el bit de menor peso vale 1 nos encontraremos ante un número impar.
- Si añadimos ceros por la izquierda a un número binario, el número no cambia.
- Si añadimos ceros por la derecha a un número binario lo estamos multiplicando por dos.
- Si el número que es todo unos, una forma rápida de calcular su valor es calcular el siguiente número y restarle uno a posteriori. Es decir, si tengo que obtener el valor de 111111, puedo calcular el valor de 1000000 que es 64 y restarle uno obteniendo que (111111)2 = (63)10.

{:.subsection}
### Binario a decimal
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/IQpDcrMrlsE?si=i8YMvAW32Mn1d1nz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

{:.section}
## Pasar de decimal a binario
Para convertir un número decimal a binario, debes realizar una serie de divisiones y anotar los restos en cada paso hasta que el cociente sea igual a 0. Aquí tienes un procedimiento paso a paso:

Supongamos que deseas convertir el número decimal 45 a binario:

Divide el número decimal por 2.
- 45 ÷ 2 = 22 (cociente) con un resto de 1
- Anota el resto (1) a la derecha.

Divide el cociente resultante en el paso anterior (22) por 2.
- 22 ÷ 2 = 11 (cociente) con un resto de 0
- Anota el resto (0) a la derecha del resto anterior.

Continúa dividiendo el cociente en cada paso por 2 y anotando los restos hasta que obtengas un cociente de 0. Continúa con los pasos anteriores:
- 11 ÷ 2 = 5 (cociente) con un resto de 1
- 5 ÷ 2 = 2 (cociente) con un resto de 1
- 2 ÷ 2 = 1 (cociente) con un resto de 0
- 1 ÷ 2 = 0 (cociente) con un resto de 1

Ahora, escribe los restos en orden inverso, desde abajo hacia arriba. Esto te dará la representación en binario del número decimal.
Los restos en orden inverso son 101101.
Entonces, el número decimal 45 se convierte en el número binario 101101.

En resumen, para convertir un número decimal a binario, divide sucesivamente el número por 2, anotando el resto en cada paso hasta que el cociente sea 0. Luego, escribe los restos en orden inverso para obtener la representación en binario.

{:.section}
### Decimal a binario
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/QqVcxYR8Zb8?si=1qgz6JcsIggIzzJZ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Pasar de hexadecimal a binario
Para convertir un número hexadecimal a binario, primero debes comprender la relación entre estos dos sistemas numéricos y luego seguir estos pasos:

Convierte cada dígito hexadecimal en su equivalente binario. Aquí está la tabla de conversión:

| <sup>Hexadecimal</sup> | <sup>Binario</sup> |
| 0 | 0000 |
| 1 | 0001 |
| 2 | 0010 |
| 3 | 0011 |
| 4 | 0100 |
| 5 | 0101 |
| 6 | 0110 |
| 7 | 0111 |
| 8 | 1000 |
| 9 | 1001 |
| A | 1010 |
| B | 1011 |
| C | 1100 |
| D | 1101 |
| E | 1110 |
| F | 1111 |

Divide el número hexadecimal en dígitos y reemplaza cada dígito con su equivalente binario. Por ejemplo, si tienes el número hexadecimal "3A7", lo descompones en dígitos y lo conviertes en binario:

3 en hexadecimal es 0011 en binario.
A en hexadecimal es 1010 en binario.
7 en hexadecimal es 0111 en binario.
Concatena los valores binarios resultantes para obtener el número binario equivalente al número hexadecimal original. En este ejemplo, tendrías:

3A7 en hexadecimal es igual a 0011 1010 0111 en binario.
Así que, has convertido con éxito el número hexadecimal "3A7" en su representación binaria "001110100111".

Este proceso es bastante directo, ya que cada dígito hexadecimal tiene una representación binaria fija, lo que facilita la conversión.

### Hexadecimal a binario
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/s_cO5svy1KY?si=W-Tzdv0ly0-Vo9_x" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Pasar de binario a hexadecimal
Para convertir un número binario a hexadecimal, debes seguir un proceso similar al de la conversión de binario a decimal, pero en lugar de agrupar en potencias de 2 como en el sistema decimal, agruparás los dígitos binarios en grupos de cuatro para obtener su equivalente hexadecimal. Aquí tienes un paso a paso:

- Divide el número binario en grupos de cuatro dígitos, comenzando desde la derecha y agregando ceros a la izquierda si es necesario para que cada grupo tenga cuatro dígitos. Si el número de dígitos binarios no es múltiplo de cuatro, agrupa los dígitos restantes en el primer grupo.

- Luego, convierte cada grupo de cuatro dígitos binarios en su equivalente hexadecimal utilizando la siguiente tabla de conversión:

| <sup>Hexadecimal</sup> | <sup>Binario</sup> |
| 0 | 0000 |
| 1 | 0001 |
| 2 | 0010 |
| 3 | 0011 |
| 4 | 0100 |
| 5 | 0101 |
| 6 | 0110 |
| 7 | 0111 |
| 8 | 1000 |
| 9 | 1001 |
| A | 1010 |
| B | 1011 |
| C | 1100 |
| D | 1101 |
| E | 1110 |
| F | 1111 |

- Escribe el valor hexadecimal resultante para cada grupo de cuatro dígitos binarios y colócalos juntos en orden desde la izquierda hasta la derecha para formar el número hexadecimal.

Ejemplo:

Supongamos que tenemos el número binario "110101101011". Lo dividimos en grupos de cuatro:
"1101 0110 1011"

Ahora, convertimos cada grupo en su equivalente hexadecimal:

| 1101 | 0110 | 1011 |
| D | 6 | B |

Finalmente, juntamos los valores hexadecimales:

Entonces, el número binario "110101101011" es igual a "D6B" en hexadecimal.
### Binario a hexadecimal
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/uQaLpYDCkAA?si=_5WKbAwrg0VHgLKF" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>