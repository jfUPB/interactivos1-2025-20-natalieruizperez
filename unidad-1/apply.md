# Unidad 1

## 🛠 Fase: Apply

### Actividad 05

Vamos a crear un programa en el micro:bit que tenga un input (un botón) y un output (enviar un mensaje por serial) que indique que se ha presionado el botón. Estás son las notas que tomé a medida que explorabamos el código, éste no está completo ya que sucede si el botón fue presionado.

##### En el microbit:
~~~
  from microbit import *          // Importar bibliotecas

  uart.init(baudrate=115200)      // Nombre del objeto que representa las comunicaciones seriales, permite enviar datos al dispositivo

  while True:
      if button_a.was_pressed():  // Si el boton fue presionado
          uart.write('A')  
~~~

##### En el p5js:
~~~
let port;                //Variables globales para que se puedan acceder desde cualquier parte
let connectBtn;

function setup() {                                       //Funcion qu ese ejecuta una sola vez
    createCanvas(400, 400);                              //Crea el canvas
    background(220);                                     //Define el color del fondo
    port = createSerial();                               //Objeto que permite hacer comunicaciones seriales
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

~~~

A la hora de analizar este código en clase nos dimos cuenta que cambiaba a una gran velocidad entre colores y se podía observar por una milésima de segundo el color rojo. Esto sucedía porque la instrucción en el microbit era si el botón fue presionado lo que causaba que no se pudiese notar bien la diferencia al presionar o no presionar el botón.  

Ahora voy a analizar el código completo y funcional que sí permite ver la diferencia cuando el botón está siendo presionado y cuando no.

##### microbit
~~~
from microbit import *        

uart.init(baudrate=115200)

while True:

    if button_a.is_pressed():  // Para que sera siempre que esté presionado
        uart.write('A')
    else:
        uart.write('N')

    sleep(100)        // Ya no funciona a 60 fps si no a 10 fps
~~~
##### ps5j
~~~
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
      port.clear();                         // Limpia el puerto serie
      connectionInitialized = true;         // Si no está conectado que se conecte
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

~~~
##### Explica cómo funciona el sistema físico interactivo que acabamos de crear.
El programa permite crear una conexión entre el microbit y el pc de forma tal que al presionar un botón en el microbit el cuadrado verde que aparece en la pantalla cambia a rojo, siempre y cuando el botón A esté siendo presionado. En este sistema los inputs serían los botones y el cable que permite conectar el microbit al pc (serial). Los outputs serían lo que se ve en la patalla del computador como el cuadrado rojo y verde, también el botón que aparece en la pantalla para conectar o desconectar el microbit.

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

