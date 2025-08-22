# Unidad 3


## 🛠 Fase: Apply

### Actividad 07

Este es el primer código que hice pensando en crear botones como los del microbit e intente hacer una función para clickear el botón, para comprobarlo quería que se mostrara un texto pero no funcionó por lo que escuché que se podía de hacer de otra forma y esta era con las teclas del computador.

``` 
let port;
let connectBtn;
let connectionInitialized = false;
let count = 20;

let validChars = "ABST";

function setup() {
  createCanvas(400, 400);
  background(220);
  port = createSerial();
  connectBtnA = createButton("A");
  connectBtnA.position(100, 300);
  connectBtnB = createButton("B");
  connectBtnB.position(150, 300);
  connectBtnS = createButton("S");
  connectBtnS.position(200, 300);
  connectBtnT = createButton("T");
  connectBtnT.position(250, 300);

}



function draw() {
  background(220);
 

  textAlign(CENTER);
  text("Press A,B,S,T to simulate micro:bit keys", width / 2, 350);
  
textAlign(CENTER);
  text(count, width / 2, height / 2);
  
  function connectBtnAClick (){
     text("hola mundo" ,width / 2, height / 2) }
  
}
```

Ahora en este código le hice cambio, le quité la conexión al serial porque no la necesita ya que es para probarlo exclusivamente en p5.js, puse para que fuese posible interacturar con la bomba con teclas en lugar de botones y también en la función setup la usé como el estado init que define todas las variables al inicio del código sin eventos.

**Código**

```
let state;
let count;         
let password = [];
let keys = [];
let keyIndex;
let startTime;

// Es como si fuese init
function setup() {
  createCanvas(400, 400);
  background(220); 
  count = 20;    
  state = "CONFIG";
  password = ['A', 'B', 'A'];
  keyIndex = 0;
  startTime = millis();
}


function draw() {
  background(220);  

  if (state === "CONFIG") {
    textAlign(CENTER);
    text("Apreta A para aumentar el tiempo", width / 2, 320);
    text("Apreta B para disminuir el tiempo", width / 2, 340);
    text("Apreta S para armar", width / 2, 360);
  } 
  
  else if (state === "ARMED") {
    text("La bomba esta armada", width / 2, 340);

    if (millis() - startTime > 1000) {
      startTime = millis();
      count--;
      if (count <= 0) {
        count = 0;
        state = "EXPLODED";
      }
    }
  } 
  
  else if (state === "EXPLODED") {
    text("La bomba explotó", width / 2, 340);
    text("Apreta T para reiniciar", width / 2, 360);
  }

  //La dejo por fuera para q se actualice cada frame
  text(count, width / 2, height / 2);
}

//Cuando se presiona una tecla se convierte en mayúscula
function keyPressed() {
  let k = key.toUpperCase();

  //Para sumar o restar los segundos
  if (state === "CONFIG") {
    if (k === 'A') {
      count = min(count + 1, 60);
    } 
    
    else if (k === 'B') {
      count = max(count - 1, 10);
    } 
    
    //Si se apreta S transiciona a ARMED
    else if (k === 'S') {
      startTime = millis();
      state = "ARMED";
      keys = [];
      keyIndex = 0;
    }
    
  } 
  
  //Si se presiona A o B que se guarde la tecla que se presionó
  else if (state === "ARMED") {
    if (k === 'A' || k === 'B') 
    {
      keys[keyIndex] = k;
      keyIndex++;
      checkPassword();
    }
  } 
  
  //Si explota y se presiona T transiciona al estado CONFIG
  else if (state === "EXPLODED") {
    if (k === 'T') {
      count = 20;
      state = "CONFIG";
    }
  }
}

  
//Función para revisar si se presionaron las tres teclas
function checkPassword() {
  // Si ya se apretaron todas las teclas de la clave, se revisa si está correcta
  if (keyIndex === password.length) {
    let correct = true;
    for (let i = 0; i < password.length; i++) {
      if (keys[i] !== password[i]) {
        correct = false;
        break;
      }
    }

    //Si la contraseña es correcta se desactiva la bomba y se reinicia el contador
    if (correct) {
      count = 20;
      keys = [];
      keyIndex = 0;
      state = "CONFIG";
    } 
    
    //Si no se reinicia la variable que se encarga de verificar cuantos caracteres se escriben para volver a intentarlo
    else {
      keys = [];
      keyIndex = 0;
    }
  }
}

```

### Actividad 07



