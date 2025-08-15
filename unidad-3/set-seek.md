# Unidad 3

## 🔎 Fase: Set + Seek

### Actividad 01
Hecha en clase

from microbit import *
import utime

class Semaforo:
    def _init_(self,tr,ta,tv,col):
        self.tr = tr 
        self.ta = ta 
        self.tv = tv
        self.col = col 
        display.set_pixel(self.col,0,9)
        self.startTime = utime.ticks_ms()
        self.state = "WAITINRED"

        
    def update(self):
        if self.state == "WAITINRED":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) >= self.tr:
                display.set_pixel(self.col,0,0)
                display.set_pixel(self.col,1,9)
                self.startTime =utime.ticks_ms()
                self.state = "WAITINYELLOW"
            
        elif self.state == "WAITINYELLOW":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) >= self.ta:
                display.set_pixel(self.col,1,0)
                display.set_pixel(self.col,2,9)
                self.startTime =utime.ticks_ms()
                self.state = "WAITINGREEN"
                
        elif self.state == "WAITINGREEN":
            if utime.ticks_diff(utime.ticks_ms(),self.startTime) >= self.tv:
                display.set_pixel(self.col,2,0)
                display.set_pixel(self.col,0,9)
                self.startTime =utime.ticks_ms()
                self.state = "WAITINRED"
        
semaforo1 = Semaforo(5000,2000,3000,0)
semaforo2 = Semaforo(3000,1000,2000,2)
semaforo3 = Semaforo(4000,3000,2000,4)

while True:
    semaforo1.update()
    semaforo2.update()
    semaforo3.update()

---

### Actividad 02
Vas a retomar la bomba de la unidad anterior y le adicionarás algunas funcionalidades:
  -Una vez la bomba esté armada es posible desactivarla con la secuencia botón A, botón B, botón A.
  -Si la secuencia se ingresa correctamente la bomba pasará de nuevo al modo de configuración de lo contrario continuará la fatal cuenta regresiva.

---

### Actividad 03

Estado en q estoy evento que voy a rpobar que acciones van a oucrrir y a que estado debe de pasar

### Actividad 05
**1. Construye el modelo de la bomba 3.0. Como ya tienes el código puedes tener un modelo muy preciso.**

**Estados**

Los estados seran CONFIG que es el estado inicial donde se puede cambiar el tiempo. Luego está ARMED que es cuando empieza la cuenta regresiva y donde se puede desactivar la bomba si se presionan los botones que son y por último esta EXPLODED que ocurre cuando el contador llega a 0 y se reinciia con el evento T.

**Eventos**
Los eventos ser'ian

Eventos
