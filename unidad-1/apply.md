# Unidad 1

## 🛠 Fase: Apply

### Actividad 05
En clase seguimos las instrucciones para crear un programa en el micro:bit que tenga un input (un botón) y un output (enviar un mensaje por serial) que indique que se ha presionado el botón. Estás son las notas que tomé a medida que explorabamos el código, este no está completo ya que sucede si el botón fue presionado.

##### En el microbit:

``` py

  from microbit import *     # Importar bibliotecas

  uart.init(baudrate=115200)    # Nombre del objeto que representa las comunicaciones seriales, permite enviar datos al dispositivo

  while True:
      if button_a.was_pressed():  # Si el boton fue presionado
          uart.write('A')  
```

##### En el p5js:

``` js

let port;                //Variables globales para que se puedan acceder desde cualquier parte
let connectBtn;

function setup() {                                       // Función que se ejecuta una sola vez
    createCanvas(400, 400);                              // Crea el canvas
    background(220);                                     // Define el color del fondo
    port = createSerial();                               // Objeto que permite hacer comunicaciones seriales
    connectBtn = createButton('Connect to micro:bit');   // Crea un boton para comunicarme con el ui
    connectBtn.position(80, 300);                        // Pone el boton en la posición
    connectBtn.mousePressed(connectBtnClick);            // Cuando se presione con el mouse llama esa funcion
}

function draw() {

  if (port.availableBytes() > 0) {
      let dataRx = port.read(1);
      if (dataRx == "A") {        // Si el botón A fue presionado
        fill("red");
      } else if (dataRx == "N") {
        fill("green");            // Si no me han llegado datos pinta en verde
      }
    }

}

  //Pintar rectángulos
  rectMode(CENTER);
    rect(width / 2, height / 2, 50, 50);

    //Actualiza la interfaz de usuario
    if (!port.opened()) {
      connectBtn.html("Connect to micro:bit");
    } else {
      connectBtn.html("Disconnect");
    }
  }

function connectBtnClick() {
    if (!port.opened()) {        // Si no está abierto el puerto
        port.open('MicroPython', 115200);
    } else {
        port.close();           // Si estaba abierto se cierra
    }
}

```

A la hora de analizar este código en clase nos dimos cuenta que cambiaba a una gran velocidad entre colores y se podía observar por una milésima de segundo el color rojo. Esto sucedía porque la instrucción en el microbit era si el botón fue presionado lo que causaba que no se pudiese notar bien la diferencia al presionar o no presionar el botón.  

  Ahora voy a analizar el código completo y funcional que sí permite ver la diferencia cuando el botón está siendo presionado y cuando no.

##### microbit

``` py
from microbit import *        

uart.init(baudrate=115200)

while True:

    if button_a.is_pressed():  // Para que sera siempre que esté presionado
        uart.write('A')
    else:
        uart.write('N')

    sleep(100)        // Ya no funciona a 60 fps si no a 10 fps
```
##### ps5j

``` js
  let port;                      // Variables globales para que se puedan acceder desde cualquier parte
  let connectBtn;
  let connectionInitialized = false;
 
  function setup() {            // Funcion qu ese ejecuta una sola vez
    createCanvas(400, 400);     // Crea un canvas
    background(220);            // Define el color del fondo
    port = createSerial();      //Objeto que permite hacer comunicaciones seriales
    connectBtn = createButton("Connect to micro:bit");  // Crea un boton para comunicarme con el ui
    connectBtn.position(80, 300);                      // Pone el boton en la posición
    connectBtn.mousePressed(connectBtnClick);         // Cuando se presione con el mouse llama esa funcion
  }

  function draw() {            
    background(220);        // Para que se actualice el fondo 

    if (port.opened() && !connectionInitialized) {  // Para ver si el puerto está abierto y conectado
      port.clear();                         // Limpia el puerto 
      connectionInitialized = true;         // Si no está conectado, se conecta
    }

    if (port.availableBytes() > 0) {   //Llegaron datos? Si es una A pone un rojo, si es una N pone un rojo
      let dataRx = port.read(1);
      if (dataRx == "A") {
        fill("red");
      } else if (dataRx == "N") {
        fill("green");
      }
    }

    //Pintar rectángulos
    rectMode(CENTER);
    rect(width / 2, height / 2, 50, 50);

    // Actualiza el texto del botón 
    if (!port.opened()) {
      connectBtn.html("Connect to micro:bit");        // Si no está abierto el puerto muestra el texto para conectarlo
    } else {
      connectBtn.html("Disconnect");                  // Si  está abierto el puerto muestra el texto para desconectarlo
    }
  }

  // Pasa cuando se presiona el botón
  function connectBtnClick() {

    // Si no está abierto se abre una conexión con el puerto
    if (!port.opened()) {                      
      port.open("MicroPython", 115200);
      connectionInitialized = false;     // Reinicia conexión
    } else {
      port.close();         // Si el puerto está abierto lo cierra
    }
  }

```

##### Explica cómo funciona el sistema físico interactivo que acabamos de crear.
El programa permite crear una conexión entre el microbit y el pc de forma tal que al presionar un botón en el microbit el cuadrado verde que aparece en la pantalla cambia a rojo, siempre y cuando el botón A esté siendo presionado. En este sistema los inputs serían los botones y el cable que permite conectar el microbit al pc (serial). Los outputs serían lo que se ve en la patalla del computador como el cuadrado rojo y verde, también el botón que aparece en la pantalla para conectar o desconectar el microbit.

---
### Actividad 06
##### Crea un programa en p5.js que muestre un círculo en la pantalla. Utiliza los botones A y B del micro:bit para controlar la posición en x del círculo en el canvas de p5.js.
Para crear este código tuve en cuenta el código que analicé en la actividad pasada solo que está vez en lugar de ser un cuadrado cree un círculo como indicaba la actividad. También añadí en la parte del microbit lo que pasaría si se presiona el botón B. Para el código e p5.js cree una variable que fuese la posición del círculo y la modifiqué cuando fuesen presionados los botones, haciendo que se restaran o sumaran valores según el caso.

##### Escribe el enlace a tu programa en el editor de p5.js.
https://editor.p5js.org/natalieruizperez/sketches/irnOR3IhA

##### Copia el código del micro:bit en la bitácora (recuerda insertarlo usando markdown y el lenguaje python).
microbit

``` py
from microbit import *             // Importar bibliotecas

uart.init(baudrate=115200)         // Nombre del objeto que representa las comunicaciones seriales, permite enviar datos al dispositivo


while True:

    if button_a.was_pressed():     // Si el botón A fue presionado escribe A
        uart.write('A')
    if button_b.was_pressed():     // Si el botón B fue presionado escribe B
        uart.write('B')

    sleep(100)                     // Ya no funciona a 60 fps si no a 10 fps
```

##### Copia el código de tu programa en la bitácora (recuerda insertarlo usando markdown y el lenguaje javascript).
psj5

``` js

//Variables globales
let port;
let connectBtn;
let connectionInitialized = false;
let x;  

function setup() {
  createCanvas(400, 400);     // Crea el canva 
  x = 200                     // Posición del círculo
  port = createSerial();      //Objeto que permite hacer comunicaciones seriales
  connectBtn = createButton("Connect to micro:bit");     // Crea un boton para comunicarme con el ui
  connectBtn.position(80, 300);                          // Pone un botón en esa posición
  connectBtn.mousePressed(connectBtnClick);              // Cuando se presione con el mouse llama esa funcion
}

function draw() {
  background(220);             //Actualiza el fondo cada frame

 // Para ver si el puerto está abierto y conectado
  if (port.opened() && !connectionInitialized) {
    port.clear();                                // Limpia el puerto             
    connectionInitialized = true;                // Si no está conectado, se conecta
  }

  if (port.availableBytes() > 0) {              //Llegaron datos? 
    let dataRx = port.read(1);
    if (dataRx == "A") {                        // Si es una A modifica la posión actual del círculo y le resta 5
      x -= 5;  
    } else if (dataRx == "B") {                 // Si es una B modifica la posión actual del círculo y le suma 5
      x += 5;  
    }
  }

  // Para crear el círculo
  fill("pink");             // Para rellenar el círculo
  circle(x, 200, 100);      // La posición en la que se crea el círculo

  if (!port.opened()) {                      
    connectBtn.html("Connect to micro:bit");   // Si no está abierto el puerto muestra el texto para conectarlo
  } else {
    connectBtn.html("Disconnect");              // Si  está abierto el puerto muestra el texto para desconectarlo
  }
}

// Pasa cuando se presiona el botón
function connectBtnClick() {
  if (!port.opened()) {                  // Si no está abierto se abre una conexión con el puerto
    port.open("MicroPython", 115200);
    connectionInitialized = false;       // Reinicia conexión
  } else {
    port.close();                        // Si el puerto está abierto lo cierra
  }
}
```

El programa permite crear una conexión entre el microbit y el pc de forma tal que después de presionar el botón A en el microbit el círculo rosado que aparece en la pantalla se le modifique la posición actual, haciendo que vaya hacia la izquierda de la pantalla. En el caso de presionar el botón B en el microbit el círculo rosado irá hacia el lado derecha de la pantalla. En este sistema los inputs serían los botones y el cable que permite conectar el microbit al pc (serial). Los outputs serían lo que se ve en la patalla del computador como el círculo rosado, cuando se actualiza la posición de este mismo y también el botón que aparece en la pantalla para conectar o desconectar el microbit.


