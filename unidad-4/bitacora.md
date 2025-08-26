# Evidencias de la unidad 4

---
### Notas de clase y actvidades

**Actividad 01**

https://editor.p5js.org/generative-design/sketches/HJ3gqcq6kN

Me gustó mucho este código, al principio cuando lo ví pensé que funcionaba de forma aleatoria pero luego de explorar en p5js me di cuenta de que su funcionamiento tiene una lógica. Al moverme de derecha a izquierda con el mouse le cambio el grosor a un conjunto de líneas, x+ para agrandar y x- para volverlas delgadas. Lo mismo pasa con un conjunto de líneas solo que estas se modifican al usar y- para aumentar el grosor y y+ para que sean más delgadas. El poder encontrar orden en algo que inicialmente no lo tenía me llamó la atención.

---

**Actividad 2**

<img width="909" height="783" alt="image" src="https://github.com/user-attachments/assets/7c93e35c-45e1-4d75-871c-a663f486af96" />

Este sketch es diferente al que me había llamado la atención ya que solamente pinta cuando se apreta el mouse. Si dejo presionado el mouse me doy cuenta que crea una circunferencia en un tiempo determinado la cual sirve a la hora de pintar.

---
**Actividad 03**
```js
# Imports go at the top
from microbit import *

uart.init(115200)           #Para iniciar la conexión
display.set_pixel(0,0,9)    #Los pixeles empiezan ensendidos      

while True:
    xValue = accelerometer.get_x()     #Si se agita horizontalmete
    yValue = accelerometer.get_y()     #Si se agita verticalmente
    aState = button_a.is_pressed()     #Si se presiona a
    bState = button_b.is_pressed()     #Si se presiona b
    data = "{},{},{},{}\n".format(xValue, yValue, aState,bState)    #Los corchetes se ponen así para en ese lugar sep onga en orden lo que le sigue al a derecha
    uart.write(data)    #Escribe en el orden de arriba los datos como texto
    sleep(100) # Envia datos a 10 Hz      #Esto es para que el sistema no se sature si apreto muchas cosas a la vez, asi hay una pausa entre cada acción
```

**¿Qué información se está enviando? ¿Cómo se está enviando?**

Se envía por medio del uart al presionar un botón o agitarlo.

**Qué significa esta parte del código: "{},{},{},{}\n".format(xValue, yValue, aState,bState)**

**Observa en la aplicación SerialTerminal cómo se ven los datos que se están enviando. ¿Qué puedes inferir de la estructura de los datos?**

La recepción de datos se hace después de hacer la conexión serial, recibe datos que se muestran en HEX y cada uno de estos valores. Pr la página de "asciitable.com" se pueden traducir estos datos ya que cada número equivale a algo.

**¿Por qué se separan los datos con comas y se termina con un salto de línea?**
Los datos se separan para qué el programa sepa que son independientes y se termina con un salto de línea para que sepa que ahí finaliza la instrucción.

**¿Qué crees que pasaría si no se separan los datos con comas y no terminan con un salto de línea?**
El programa lo tomaría como un mismo valor por lo que no lograriíamos nuestro propósito y además habría error. El 0 indica que ya se puede procesar, sin el salto de línea no habría forma de que el programa sepa que se debe de procesar.                                               
**Para qué crees que se usa la función sleep(100)? ¿Qué pasaría si no se usara?**


**Observa cómo cambian los valores de xValue y yValue a medida que el micro:bit se inclina hacia la izquierda, derecha, adelante y atrás. ¿Qué valores toman xValue y yValue en cada caso?**

**¿Qué valores toman aState y bState cuando presionas los botones A y B?**

**Observa qué ocurre si en vez de is_pressed() usas was_pressed(). ¿Qué diferencias encuentras?**

---
## Código


[Enlace a la aplicación a modificar](URL)

Código a modificar:

``` js

```

[Enlace a la aplicación modificada](URL)

Código modificado:

``` js

```

## Video

[Video demostratativo](URL)



