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
    connectBtn = createButton('Connect to micro:bit');   //
    connectBtn.position(80, 300);
    connectBtn.mousePressed(connectBtnClick);
}

function draw() {
}

function connectBtnClick() {
    if (!port.opened()) {
        port.open('MicroPython', 115200);
    } else {
        port.close();
    }
}

~~~
