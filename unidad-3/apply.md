# Unidad 3


## 🛠 Fase: Apply


### Actividad 06

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


### Actividad 07
