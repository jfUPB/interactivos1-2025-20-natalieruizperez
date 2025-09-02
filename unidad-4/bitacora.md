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

**1. ¿Qué información se está enviando? ¿Cómo se está enviando?**

Se envía por medio del uart al presionar un botón o agitarlo.

**2. Qué significa esta parte del código: "{},{},{},{}\n".format(xValue, yValue, aState,bState)**
En el código se mostraran esos valores en el orden que aparecen en los corchetes. Es para que se empaqueten los datos.

**3. Observa en la aplicación SerialTerminal cómo se ven los datos que se están enviando. ¿Qué puedes inferir de la estructura de los datos?**

La recepción de datos se hace después de hacer la conexión serial, recibe datos que se muestran en HEX y cada uno de estos valores. Pr la página de "asciitable.com" se pueden traducir estos datos ya que cada número equivale a algo.

**4. ¿Por qué se separan los datos con comas y se termina con un salto de línea?**

Los datos se separan para qué el programa sepa que son independientes y se termina con un salto de línea para que sepa que ahí finaliza la instrucción.

**5. ¿Qué crees que pasaría si no se separan los datos con comas y no terminan con un salto de línea?**
El programa lo tomaría como un mismo valor por lo que no lograriíamos nuestro propósito y además habría error. El 0 indica que ya se puede procesar, sin el salto de línea no habría forma de que el programa sepa que se debe de procesar.   

**Para qué crees que se usa la función sleep(100)? ¿Qué pasaría si no se usara?**

Se usa para que no se puedan enviar muchos datos al mismo tiempo, si no se usa se saturaría el sistema.

**6. Observa cómo cambian los valores de xValue y yValue a medida que el micro:bit se inclina hacia la izquierda, derecha, adelante y atrás. ¿Qué valores toman xValue y yValue en cada caso?**



**7. ¿Qué valores toman aState y bState cuando presionas los botones A y B?**


**8. Observa qué ocurre si en vez de is_pressed() usas was_pressed(). ¿Qué diferencias encuentras?**
El is_pressed() es cuando se presiona y el was_pressed() es en el momento en el que se suelta.

 **9. Si el micro:bit tiene los siguientes datos xValue: 969, yValue: 652, aState: True, bState: False ¿Qué bytes se enviarían por el puerto serial?**

39 (6) 36 (9) 35 (6) 2c (la coma)

  36  35 32 2C (la coma)
  
  54 (T) 72 (r) 75 (u) 65 (e) 2C (coma) 
  
  46 (F) 61 (a) 6C (l) 73 (s) 65 (e) 0a (carácter especial el de la n)

---
## Código


[Enlace a la aplicación a modificar](https://editor.p5js.org/natalieruizperez/sketches/k9jxszUXB)

Código a modificar:

``` js
// P_2_1_1_01
//
// Generative Gestaltung – Creative Coding im Web
// ISBN: 978-3-87439-902-9, First Edition, Hermann Schmidt, Mainz, 2018
// Benedikt Groß, Hartmut Bohnacker, Julia Laub, Claudius Lazzeroni
// with contributions by Joey Lee and Niels Poldervaart
// Copyright 2018
//
// http://www.generative-gestaltung.de
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

/**
 * changing strokeweight and strokecaps on diagonals in a grid
 *
 * MOUSE
 * position x          : left diagonal strokeweight
 * position y          : right diagonal strokeweight
 * left click          : new random layout
 *
 * KEYS
 * 1                   : round strokecap
 * 2                   : square strokecap
 * 3                   : project strokecap
 * s                   : save png
 */
'use strict';

var tileCount = 20;
var actRandomSeed = 0;

var actStrokeCap;

function setup() {
  createCanvas(600, 600);

  actStrokeCap = ROUND;
}

function draw() {
  clear();
  strokeCap(actStrokeCap);

  randomSeed(actRandomSeed);

  for (var gridY = 0; gridY < tileCount; gridY++) {
    for (var gridX = 0; gridX < tileCount; gridX++) {

      var posX = width / tileCount * gridX;
      var posY = height / tileCount * gridY;

      var toggle = int(random(0, 2));

      if (toggle == 0) {
        strokeWeight(mouseX / 20);
        line(posX, posY, posX + width / tileCount, posY + height / tileCount);
      }
      if (toggle == 1) {
        strokeWeight(mouseY / 20);
        line(posX, posY + width / tileCount, posX + height / tileCount, posY);
      }
    }
  }
}

function mousePressed() {
  actRandomSeed = random(100000);
}

function keyReleased() {
  if (key == 's' || key == 'S') saveCanvas(gd.timestamp(), 'png');

  if (key == '1') actStrokeCap = ROUND;
  if (key == '2') actStrokeCap = SQUARE;
  if (key == '3') actStrokeCap = PROJECT;
}

```

[Enlace a la aplicación modificada](https://editor.p5js.org/natalieruizperez/sketches/o28_TX1ex)

Código modificado:

``` js
let tileCount = 20;
let actRandomSeed = 0;
let actStrokeCap;

let port;
let connectBtn;

let microbitX = 0;
let microbitY = 0;
let buttonA = 0;
let buttonB = 0;

let lastBState = 0;
let incomingData = '';  // Para acumular la línea recibida

function setup() {
  createCanvas(600, 600);
  background(255);

  actStrokeCap = ROUND;

  port = createSerial();

  connectBtn = createButton('Connect to micro:bit');
  connectBtn.position(80, height + 20);
  connectBtn.mousePressed(connectBtnClick);
}

function draw() {
  clear();
  strokeCap(actStrokeCap);
  randomSeed(actRandomSeed);

  let mappedX = map(microbitX, -1024, 1024, 0, width);
  let mappedY = map(microbitY, -1024, 1024, 0, height);

  for (let gridY = 0; gridY < tileCount; gridY++) {
    for (let gridX = 0; gridX < tileCount; gridX++) {
      let posX = (width / tileCount) * gridX;
      let posY = (height / tileCount) * gridY;

      let toggleState = int(random(0, 2));

      if (toggleState === 0) {
        strokeWeight(mappedX / 20);
        line(posX, posY, posX + width / tileCount, posY + height / tileCount);
      } else {
        strokeWeight(mappedY / 20);
        line(posX, posY + width / tileCount, posX + height / tileCount, posY);
      }
    }
  }

  // Leer datos seriales 
  let data = port.readUntil('\n');
  if (data) {
    data = data.trim();
    if (data.length > 0) {
      let parts = data.split(",");
      if (parts.length >= 4) {
        microbitX = int(parts[0]);
        microbitY = int(parts[1]);
        buttonA = parts[2].trim().toLowerCase() === "true" ? 1 : 0;
        buttonB = parts[3].trim().toLowerCase() === "true" ? 1 : 0;
      }
    }
  }

  // Cambiar la seed al apretar A, simula el click izquierdo del código original
  if (buttonA === 1 && lastAState === 0) {
    actRandomSeed = random(100000);  // Cambia la semilla para un nuevo patrón
    strokeCap(actStrokeCap);
  }
  lastAState = buttonA;
  
  // Guardar imagen al apretar el boton B, simula lo que pasa al apretar la tecla s en el código original
  if (buttonB === 1 && lastBState === 0) {
    saveCanvas('screenshot', 'png');
  }
  lastBState = buttonB;

  // Actualizar texto
  if (!port.opened()) {
    connectBtn.html('Connect to micro:bit');
  } else {
    connectBtn.html('Disconnect');
  }
}

function connectBtnClick() {
  if (!port.opened()) {
    port.open('MicroPython', 115200);
  } else {
    port.close();
  }
}

```

## Video

[Video demostratativo](URL)


---

### Proceso código 

Primero lo que hice fue analizar este código que es el de la página y leer en qué consistía. El mismo código explica en qué consite. Veo que cuano se mueve el mouse horizontalmente el grosor de las líneas diagonales izquierdas cambian. También que pasa lo mismo pero las líneas diagonales derechas al mover el mouse verticalmente. Veo que al hacer click izquierdo cambia la distribución de las líneas generándose una random entonces quiero que suceda lo mismo con el microbit al apretar un botón. Además si apreto la letra s tomo una screenshot. Teniendo en cuenta esto mi plan de trabajo va a ser que al mover el microbit de derecha a izquierda suceda lo mismo que en el código y al mover el microbit de arriba hacia abajo también pase lo mismo. Voy a hacer que al apretar B se tome una screenshot y que cada vez que aprete A se cambie la distribución de las líneas a una random.







