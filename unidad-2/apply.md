# Unidad 2


## 🛠 Fase: Apply

### Actividad 04
Diseña la máquina de estados que solucione este problema: En un escape room se requiere construir una aplicación para controlar una bomba temporizada. El circuito de control de la bomba está compuesto por cuatro sensores, denominados UP (botón A), DOWN (botón B), touch (botón de touch) y ARMED (el gesto de shake de acelerómetro). Tiene dos actuadores o dispositivos de salida que serán un display (la pantalla de LEDs) y un speaker.

**Construye un diagrama detallado de la máquina de estados, incluyendo estados, eventos, transiciones y acciones.**

<img width="860" height="714" alt="image" src="https://github.com/user-attachments/assets/141d5e2b-7cd3-4ab5-b15b-d549dcc7ad82" />

**Estados**
Tiene el estado INIT que es donde se inicializa con un tiempo de 20 segundos y se prepara para configurarse. El estado CONFIG que es para modificar el tiempo de la bomba con botones. También esta El estado ARMED inicia hace la cuenta regresiva cuando que fue agitado. Por último, el estado EXPLOTION que es cuando ya explotó y reinicia el tiempo. 

**Eventos**
Serían el paso del tiempo y cuando se presionan los botones para modificarlo. También cuando se agita el microbit.

**Acciones**
Son cuando se muestra el tiempo, también cuando se activa el speaker.

### Actividad 05
Implementando la Bomba Temporizada. 

**Código**

``` py
from microbit import *
import utime

STATE_INIT = 0
STATE_CONFIG = 1
STATE_ARMED = 2
STATE_EXPLOTION = 3

explosion_time = 20
start_time = 0

state = STATE_INIT

while True:
    if state == STATE_INIT:
        explosion_time = 20
        display.show(str(explosion_time))
        state = STATE_CONFIG

    elif state == STATE_CONFIG:
        if button_a.was_pressed():
            if explosion_time < 60:
                explosion_time += 1
            display.show(str(explosion_time))

        if button_b.was_pressed():
            if explosion_time > 10:
                explosion_time -= 1
            display.show(str(explosion_time))

        if accelerometer.was_gesture("shake"):
            start_time = utime.ticks_ms()
            state = STATE_ARMED

    elif state == STATE_ARMED:
        if utime.ticks_diff(utime.ticks_ms(), start_time) > 1000:
            explosion_time -= 1
            display.show(str(explosion_time))
            start_time = utime.ticks_ms()

        if explosion_time <= 0:
            speaker.on()
            state = STATE_EXPLOTION

    elif state == STATE_EXPLOTION:
        explosion_time = 20
        display.show(str(explosion_time))
        state = STATE_CONFIG
``` 
La definición de los vectores de prueba básicos que permiten verificar el correcto funcionamiento del programa.



