
# Evidencias de la unidad 5

## Actividad 01

**1. Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?**

Se comunican a través del uart y la librería de p5.js. Los datos que envía son xValue, yValue, aState y bState

**2. ¿Cómo es la estructura del protocolo ASCII usado?**

**3. Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.**

```
  if (port.availableBytes() > 0) {
      let data = port.readUntil("\n");
      if (data) {
        data = data.trim();
        let values = data.split(",");
        if (values.length == 4) {
          microBitX = int(values[0]) + windowWidth / 2;              //Aquí se está 
          microBitY = int(values[1]) + windowHeight / 2;             //
          microBitAState = values[2].toLowerCase() === "true";       //
          microBitBState = values[3].toLowerCase() === "true";       //
          updateButtonStates(microBitAState, microBitBState);
        } else {
          print("No se están recibiendo 4 datos del micro:bit");
        }
```

**4. ¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?**


**5. Capturas de pantalla de los algunos dibujos que hayas hecho con el sketch.**
<img width="834" height="737" alt="image" src="https://github.com/user-attachments/assets/51a2da87-e3db-4a01-bc89-4b8e5edc3258" />

<img width="840" height="737" alt="image" src="https://github.com/user-attachments/assets/bb6e4c0e-53be-4d30-8af5-ab1db4d3af65" />

<img width="830" height="731" alt="image" src="https://github.com/user-attachments/assets/9a94f58a-ca2b-4cd8-8362-473c8f95a36d" />

### Preguntas luego de responder la unidad

**1. ¿Que hace exactamente uart.write? ¿Y uart.init? ¿Por qué se pone 115200? ¿Cuál de los uart es el que se comunica con el microbit y p5js? ¿Cómo funcionan?**

uart.write envía los datos del microbit a el pc conviertiendo lo que se ponga entre paréntesis en bytes. uart.init configura uart.write para que funcione correctamente. Es como una forma de prepar uart para que funcione. El número que va entre paréntesis es la velocidad de transmisión, es decir cuántos bytes se envían y tiene que coincidir entre el receptor y el emisor pero **¿cómo se cuál velocidad poner?** Según mi consulta parece que las más comunes de usar son 9600 y 115200 que es el que usamos en clase. 9600 es más lenta pero confiable mientras que 115200 rápida y se usa para proyectos avanzados. Voy a poner la velocidad de 9600 a ver si funciona el código.

<img width="890" height="441" alt="image" src="https://github.com/user-attachments/assets/80b052a8-96a8-43c4-bbee-f404f5e22e08" />

Al poner eso me doy cuenta que aunque corre el código en p5js al usar el microbit no funciona correctamente, esto es porque en el código no especifique que era una velocidad de 9600. La parte del código en p5js que me muestra exactamente la parte en donde recibe datos es la siguiente.

```
function connectBtnClick() {
  if (!port.opened()) {
    port.open("MicroPython", 115200);  // Conexión donde especifico la velocidad que va a recibir
    connectionInitialized = false;
  } else {
    port.close();
  }
}
```
En conclusión los números que ponga entre paréntesis en el uart.init son la velocidad en la que se van a mandar los bytes, por lo que en el p5js debo de poner la misma velocidad para que pueda recibir los datos correctamente.




