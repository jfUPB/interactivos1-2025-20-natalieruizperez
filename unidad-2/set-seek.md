# Unidad 2

## 🔎 Fase: Set + Seek

### Actividad 01
Analizando un programa con una máquina de estados simple.

``` js
from microbit import *
import utime

class Pixel:
    def __init__(self,pixelX,pixelY,initState,interval):
        self.state = "Init"
        self.startTime = 0
        self.interval = interval
        self.pixelX = pixelX
        self.pixelY = pixelY
        self.pixelState = initState

    def update(self):

        if self.state == "Init":
            self.startTime = utime.ticks_ms()
            self.state = "WaitTimeout"
            display.set_pixel(self.pixelX,self.pixelY,self.pixelState)

        elif self.state == "WaitTimeout":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) > self.interval:
                self.startTime = utime.ticks_ms()
                if self.pixelState == 9:
                    self.pixelState = 0
                else:
                    self.pixelState = 9
                display.set_pixel(self.pixelX,self.pixelY,self.pixelState)

pixel1 = Pixel(0,0,0,1000)
pixel2 = Pixel(4,4,0,500)

while True:
    pixel1.update()
    pixel2.update()
```

**Describe detalladamente cómo funciona este ejemplo.**
Este programa hace que dos puntos en la pantalla del micro:bit se prendan y apaguen. Cada  dónde está, si está prendido o apagado, y cuánto tiempo debe esperar antes de cambiar. Primero, el punto se prepara y se prende o apaga por primera vez. Luego, espera el tiempo que le toca. Cuando ese tiempo pasa, cambia de prender a apagar o de apagar a prender, y actualiza la pantalla. Esto se repite todo el tiempo para que los puntos parpadeen a diferentes velocidades.

**Estados**
Los estados en el programa serían las diferentes etapas en las que puede estar cada píxel. Primero está el estado init, que es cuando el píxel se prepara para empezar y se enciende o apaga por primera vez. Luego está el estado WaitTimeout, que es cuando el píxel espera a que pase el tiempo que se le indicó antes de cambiar de nuevo. Estos estados ayudan a controlar cuándo y cómo se actualiza cada píxel.

**Eventos/inputs**
Los inputs o eventos en el programa son el paso del tiempo. El programa está siempre revisando cuánto tiempo ha pasado para saber si ya debe cambiar el píxel. Cuando el tiempo que se puso como espera termina, el programa actúa y cambia el píxel.

**Acciones en el programa**
Las acciones del programa son cambiar el brillo del píxel, de apagado a prendido y viceversa, cada vez que pasa el tiempo que se espera. Después, actualiza la pantalla para mostrar ese cambio en el lugar del píxel. Cuando el tiempo que el programa espera termina, cambia cómo se ve el píxel y lo muestra.

### Actividad 02
Implementemos juntos un semáforo simple (rojo, amarillo, verde) utilizando una máquina de estados en Micropython. Representaremos cada color del semáforo con un LED del display del micro:bit.

Escribe el código que soluciona este problema en tu bitácora.

Identifica los estados, eventos y acciones en tu código.
