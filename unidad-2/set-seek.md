# Unidad 2

## 🔎 Fase: Set + Seek

### Actividad 01
Analizando un programa con una máquina de estados simple.

``` py
from microbit import *
import utime

class Pixel:
    def __init__(self,pixelX,pixelY,initState,interval):     # Definición de variables
        self.state = "Init"                         
        self.startTime = 0                      
        self.interval = interval                    
        self.pixelX = pixelX                        
        self.pixelY = pixelY                        
        self.pixelState = initState                

//Para actualizar el estado
    def update(self):                                 # Inicia el pixel y guarda el tiempo
        if self.state == "Init":                      
            self.startTime = utime.ticks_ms()         
            self.state = "WaitTimeout"                
            display.set_pixel(self.pixelX,self.pixelY,self.pixelState)  # Muestra el pixel
        elif self.state == "WaitTimeout":            # Cuando está esperando
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) > self.interval:    # Mira si ya pasó el tiempo que hay que esperar
                self.startTime = utime.ticks_ms()    # Reinicia el tiempo
                if self.pixelState == 9:             #  Si es 9 (está prendido) se apaga
                    self.pixelState = 0
                else:
                    self.pixelState = 9              # Si no está prendido se prende
                display.set_pixel(self.pixelX,self.pixelY,self.pixelState)  # Se muestra el pixel

# Objetos
pixel1 = Pixel(0,0,0,1000)
pixel2 = Pixel(4,4,0,500)

# Para que se actualice el pixel
while True:
    pixel1.update()
    pixel2.update()
```

**Describe detalladamente cómo funciona este ejemplo.**

  Este ejemplo funciona por medio de un programa que hace que dos puntos en la pantalla del micro:bit se prendan y apaguen. Todo depende si está prendido o apagado, y si pasó el tiempo de espera para poder cambiar. Primero, el pixel se prende o apaga. Luego, espera el tiempo que le toca. Cuando el tiempo pasa cambia de estado que sería de prendido a apagado o viceversa y actualiza la pantalla. Esto se repite todo el tiempo para que los puntos parpadeen a diferentes velocidades.

**Estados**

  Los estados en el programa serían las etapas del píxel. Primero init, que es cuando el píxel se prepara para empezar y se prende o apaga por primera vez. Luego está el estado WaitTimeout, que es cuando el píxel espera a que pase el tiempo que se le indicó antes de cambiar de nuevo. Estos estados ayudan a controlar cuándo y cómo se actualiza cada píxel.

**Eventos/inputs**

  Los inputs o eventos en el programa son el paso del tiempo. El programa está siempre revisando cuánto tiempo ha pasado para saber si ya debe cambiar el píxel. Cuando el tiempo que se puso como espera termina, el programa cambia el píxel.

**Acciones en el programa**

  Las acciones del programa son cambiar el brillo del píxel, de apagado a prendido y viceversa, cada vez que pasa el tiempo que se espera. Después, actualiza la pantalla para mostrar ese cambio. Cuando el tiempo que el programa espera termina, cambia el estado del píxel.

### Actividad 02
Implementemos juntos un semáforo simple (rojo, amarillo, verde) utilizando una máquina de estados en Micropython. Representaremos cada color del semáforo con un LED del display del micro:bit.

Escribe el código que soluciona este problema en tu bitácora.

Identifica los estados, eventos y acciones en tu código.
