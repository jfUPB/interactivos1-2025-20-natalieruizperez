# Unidad 3

## 🔎 Fase: Set + Seek

### Actividad 01
Hecha en clase

``` py
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
```

---

### Actividad 05
**1. Construye el modelo de la bomba 3.0. Como ya tienes el código puedes tener un modelo muy preciso.**

**Estados**

Los estados seran CONFIG que es el estado inicial donde se puede cambiar el tiempo. Luego está ARMED que es cuando empieza la cuenta regresiva y donde se puede desactivar la bomba si se presionan los botones que son y por último esta EXPLODED que ocurre cuando el contador llega a 0 y se reinciia con el evento T.  También hay otro que revisa que el tiempo actual haya pasado el intervalo.

**Eventos**

Los eventos serían cuando se presionan los botones que pueden ser A o B que sirven para sumar o restar segundos. También cuando se sacude que hace que empiece la cuenta regresiva y la T que reinicia el programa.

**Acciones**

Las acciones serían ver en la pantalla como aumenta o disminuye el tiempo, también cuando se resetea. Otra acción sería cuando muestra la calavera al llegar a 0.


**2. Crear una tabla con los vectores de prueba. La tabla debe tener 4 columnas por vector y puedes agrupar vectores en un gran vector.**
Un vector es el estado en el que estoy, el evento que voy a probar, que acciones van a ocurrir y a que estado debe de pasar.
