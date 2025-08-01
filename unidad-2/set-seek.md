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

  Los estados en el programa serían las etapas del píxel qué esperan los eventos. Primero init, que es cuando el píxel se prepara para empezar y se prende o apaga por primera vez. Luego está el estado WaitTimeout, que es cuando el píxel espera a que pase el tiempo que se le indicó antes de cambiar de nuevo. Estos estados ayudan a controlar cuándo y cómo se actualiza cada píxel.

**Eventos/inputs**

  Los inputs o eventos en el programa son el paso del tiempo. El programa está siempre revisando cuánto tiempo ha pasado para saber si ya debe cambiar el píxel. Cuando el tiempo que se puso como espera termina, el programa cambia el píxel.

**Acciones en el programa**

  Las acciones del programa son cambiar el brillo del píxel, de apagado a prendido y viceversa, cada vez que pasa el tiempo que se espera. Después, actualiza la pantalla para mostrar ese cambio. Cuando el tiempo que el programa espera termina, cambia el estado del píxel.
  
---
### Actividad 02
Implementemos juntos un semáforo simple (rojo, amarillo, verde) utilizando una máquina de estados en Micropython. Representaremos cada color del semáforo con un LED del display del micro:bit.

Escribe el código que soluciona este problema en tu bitácora.

Identifica los estados, eventos y acciones en tu código.
``` py
from microbit import *
import utime

verde_pos = (2, 0)    
rojo_pos = (2, 4)  
amarillo_pos = (2, 2)     

def encender_led(pos):
    display.set_pixel(pos[0], pos[1], 9)  

def apagar_todos():
    display.clear()


while True:
    encender_led(verde_pos)
    utime.sleep(1)  
    apagar_todos()

    encender_led(amarillo_pos)
    utime.sleep(2)  
    apagar_todos()

    encender_led(rojo_pos)
    utime.sleep(2)
    apagar_todos()
``` 

---
### Actividad 03
El programa que busca gestionar la concurrencia entre la secuencia de imágenes y la respuesta a la pulsación de botones.

``` py
from microbit import *
import utime

STATE_INIT = 0
STATE_HAPPY = 1
STATE_SMILE = 2
STATE_SAD = 3

HAPPY_INTERVAL = 1500
SMILE_INTERVAL = 1000
SAD_INTERVAL = 2000

current_state = STATE_INIT
start_time = 0
interval = 0

while True:
    # pseudoestado STATE_INIT
    if current_state == STATE_INIT:
        display.show(Image.HAPPY)
        start_time = utime.ticks_ms()
        interval = HAPPY_INTERVAL
        current_state = STATE_HAPPY
    elif current_state == STATE_HAPPY:
        if button_a.was_pressed():
            # Acciones para el evento
            display.show(Image.SAD)
            # Acciones de entrada para el siguiente estado
            start_time = utime.ticks_ms()
            interval = SAD_INTERVAL
            current_state = STATE_SAD
        if utime.ticks_diff(utime.ticks_ms(), start_time) > interval:
            # Acciones para el evento
            display.show(Image.SMILE)
            # Acciones de entrada para el siguiente estado
            start_time = utime.ticks_ms()
            interval = SMILE_INTERVAL
            current_state = STATE_SMILE
    elif current_state == STATE_SMILE:
        if button_a.was_pressed():
            display.show(Image.HAPPY)
            start_time = utime.ticks_ms()
            interval = HAPPY_INTERVAL
            current_state = STATE_HAPPY
        if utime.ticks_diff(utime.ticks_ms(), start_time) > interval:
            display.show(Image.SAD)
            start_time = utime.ticks_ms()
            interval = SAD_INTERVAL
           current_state = STATE_SAD
    elif current_state == STATE_SAD:
        if button_a.was_pressed():
            display.show(Image.SMILE)
            start_time = utime.ticks_ms()
            interval = SMILE_INTERVAL
            current_state = STATE_SMILE
        if utime.ticks_diff(utime.ticks_ms(), start_time) > interval:
            display.show(Image.HAPPY)
            start_time = utime.ticks_ms()
            interval = HAPPY_INTERVAL
            current_state = STATE_HAPPY
``` 
¿Cómo es posible estructurar una aplicación usando una máquina de estados para poder atender varios eventos de manera concurrente?
Es programación concurrente porque mientras está esperando también puede hacer otra acción, de tal forma optimiza las tareas al liberar la cpu para que muchas acciones puedan estar usando su propio código.

¿Cómo haces para probar que el programa está correcto?

**Explica por qué decimos que este programa permite realizar de manera concurrente varias tareas.**

**Identifica los estados, eventos y acciones en el programa.**

**Estados**
Son condiciones, en este caso sería al principio cuando espera que pase un segundo y medio. Otro estado sería cuando cambia a una cara sonriente y luego a la triste. Finalmente de triste pasa a happy

**Eventos**
Es como una acción que hace que algo cambie. No hay eventos en la primera parte cuando se muestra la cara feliz. Si presiono A ocurre un evento y puede cambiar el estado actual.

Es programación concurrente porque mientras está esperando también puede hacer otra acción, de tal forma optimiza las tareas al liberar la cpu para que muchas acciones puedan estar usando su propio código.

**Acciones**
Lo que sucede al realizar un evento.La acción que hace sería la cara feliz.

Describe y aplica al menos 3 vectores de prueba para el programa. Para definir un vector de prueba debes llevar al sistema a un estado, generar los eventos y observar el estado siguiente y las acciones que ocurrirán. Por tanto, un vector de prueba tiene unas condiciones iniciales del sistema, unos resultados esperados y los resultados realmente obtenidos. Si el resultado obtenido es igual al esperado entonces el sistema pasó el vector de prueba, de lo contrario el sistema puede tener un error.
