# Unidad 1

## 🛠 Fase: Apply

### Actividad 05

Vamos a crear un programa en el micro:bit que tenga un input (un botón) y un output (enviar un mensaje por serial) que indique que se ha presionado el botón.

##### En el microbit:
~~~
  from microbit import * // Importar bibliotecas

  uart.init(baudrate=115200)  // Nombre del ob jeto que representa las comunicaciones seriales

  while True:
      if button_a.was_pressed():  // Si el boton fue presionado
          uart.write('A')  
~~~

##### En el p5js:
~~~
let port;                //Variables globales para que se puedan acceder desde cualquier parte
let connectBtn;

function setup() {               //Funcion qu ese ejecuta una sola vez
    createCanvas(400, 400);      //Crea el canvas
    background(220);             //Define el valor del fondo
    port = createSerial();       //Objeto que permite hacer comunicaciones seriales
    connectBtn = createButton('Connect to micro:bit');   // Crea un boton para comunicarme con el ui
    connectBtn.position(80, 300); // Pone el boton en la posición
    connectBtn.mousePressed(connectBtnClick);  // Cuando se presione con el mouse llama esa funcion
}

function draw() {

  if (port.availableBytes() > 0) {
      let dataRx = port.read(1);
      if (dataRx == "A") {
        fill("red");
      } else if (dataRx == "N") {
        fill("green"); // Si no me han llegado datos pinta en verde
      }
    }

}

//Pintar rectangulos
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
    if (!port.opened()) {        //Si no está abierto el puerto
        port.open('MicroPython', 115200);
    } else {
        port.close();           // Si estaba abierto se cierra
    }
}

~~~

Vamos a modificiar el código y finalmente quedaría asi

##### microbit
~~~
from microbit import *

uart.init(baudrate=115200)

while True:

    if button_a.is_pressed():  //Para que sera siempre que esté presionado
        uart.write('A')
    else:
        uart.write('N')

    sleep(100)        //Ya no funciona a 60 fps si no a 10 fps
~~~
##### ps5j
~~~
  let port;
  let connectBtn;
  let connectionInitialized = false;

  function setup() {
    createCanvas(400, 400);
    background(220);
    port = createSerial();
    connectBtn = createButton("Connect to micro:bit");
    connectBtn.position(80, 300);
    connectBtn.mousePressed(connectBtnClick);
  }

  function draw() {
    background(220);

    if (port.opened() && !connectionInitialized) {  
      port.clear();
      connectionInitialized = true;
    }

    if (port.availableBytes() > 0) {   //Llegaron datos? Si es una A pone un rojo, si es una N pone un rojo
      let dataRx = port.read(1);
      if (dataRx == "A") {
        fill("red");
      } else if (dataRx == "N") {
        fill("green");
      }
    }

    rectMode(CENTER);
    rect(width / 2, height / 2, 50, 50);

    if (!port.opened()) {
      connectBtn.html("Connect to micro:bit");
    } else {
      connectBtn.html("Disconnect");
    }
  }

  function connectBtnClick() {
    if (!port.opened()) {
      port.open("MicroPython", 115200);
      connectionInitialized = false;
    } else {
      port.close();
    }
  }

~~~

El programa permite crear una conexión entre el microbit y el pc de forma que al presionar un botón en el microbit el cuadrado verde que aparece en la pantalla cambia a rojo siempre y cuando el botón A esté siendo presionado.

Cuales son los inputs de cada computador, cuales son los outputs y que procesa

### Actividad 06

Crea un programa en p5.js que muestre un círculo en la pantalla. Utiliza los botones A y B del micro:bit para controlar la posición en x del círculo en el canvas de p5.js.

##### microbit
~~~
from microbit import *

uart.init(baudrate=115200)

while True:

    if button_a.was_pressed():
        uart.write('A')
    if button_b.was_pressed():
        uart.write('B')

    sleep(100)
~~~

#psj5
~~~~
let port;
let connectBtn;
let connectionInitialized = false;
let x;  

function setup() {
  createCanvas(400, 400);
  x = 200
  port = createSerial();
  connectBtn = createButton("Connect to micro:bit");
  connectBtn.position(80, 300);
  connectBtn.mousePressed(connectBtnClick);
}

function draw() {
  background(220);

  if (port.opened() && !connectionInitialized) {
    port.clear();
    connectionInitialized = true;
  }

  if (port.availableBytes() > 0) {
    let dataRx = port.read(1);
    if (dataRx == "A") {
      x -= 5;  
    } else if (dataRx == "B") {
      x += 5;  
    }
  }

  circle(CENTER);
  fill("pink"); 
  circle(x, 200, 100);

  if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
  } else {
    connectBtn.html("Disconnect");
  }
}

function connectBtnClick() {
  if (!port.opened()) {
    port.open("MicroPython", 115200);
    connectionInitialized = false;
  } else {
    port.close();
  }
}
~~~

Cuales son los inputs de cada computador, cuales son los outputs y que procesa

