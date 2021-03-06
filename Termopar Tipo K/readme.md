Es importante entender el funcionamiento del módulo MAX6675.
Primeramente comentar que este módulo funciona por SPI.
Si observamos el datasheet podemos ver que cuando seleccionamos el dispositivo poniendo a bajo el CS el módulo nos va a enviar 16 bits con la siguiente configuración

## Trama de bits

<img src="https://github.com/antonioescamezalvarez/Ejemplos-STM32/blob/main/Termopar%20Tipo%20K/BITS.png" width="700" />

El código es tan sencillo como leer los dos bytes, unirlos en una variable uint16_t, shifftear 3 bits a la derecha (ya que no vamos a realizar ningun control) y por último leer la temperatura (el dummy sign bit siempre es 0 por lo que no nos afecta en ningún caso), el MAX6675 puede leer hasta 1024C y tiene un adc de 12 bits.... La regla de 3 que aplicamos es tan sencilla como, 1024 ---- 4095, luego nuestro valor de temperatura se calcula como la lectura * (1024/4095), si observamos algunas librerías podemos ver que sustituyen 1024/4095 por 0.25, logicamente es lo mismo, pero se entiende mas si se usa la fracción ya que indica que conversión se esta realizando.

## Transmisión Completa

<img src="https://github.com/antonioescamezalvarez/Ejemplos-STM32/blob/main/Termopar%20Tipo%20K/protocoloMAX6675.jpg" width="700" />

## Ejemplo Código
El código es tan sencillo que no se ha creado ningún tipo de librería ni se ha subido ningún codigo como tal, simplemente basta con seleccionar un SPI por defecto y añadir un GPIO_OUTPUT para el CS
<img src="https://github.com/antonioescamezalvarez/Ejemplos-STM32/blob/main/Termopar%20Tipo%20K/EjemploCodigo.png" width="700" />

Y las variables que hemos creado son las siguientes

<img src="https://github.com/antonioescamezalvarez/Ejemplos-STM32/blob/main/Termopar%20Tipo%20K/Variables.png" width="200" />

## Montaje
Por último dejo una foto del montaje para visualizar los elementos
<img src="https://github.com/antonioescamezalvarez/Ejemplos-STM32/blob/main/Termopar%20Tipo%20K/Montaje.jpg" width="700" />
