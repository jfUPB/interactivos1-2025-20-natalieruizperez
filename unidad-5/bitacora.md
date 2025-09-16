
# Evidencias de la unidad 5

## Actividad 01

**1. Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?**

Se comunican a través del uart y la librería de p5.js. Los datos que envía son xValue, yValue, aState y bState

**2. ¿Cómo es la estructura del protocolo ASCII usado?**

**3. Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.**


```js
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

## Actividad 02

Al editar el código de microbit y conectarlo al serial terminal obtengo este resultado. Eso eso es porque los datos se envían en formato binario como cadena de bytes a través del puerto serial.

**Binario**

<img width="1065" height="308" alt="image" src="https://github.com/user-attachments/assets/e7f447d3-c776-4fd4-9dfe-f076a1c8ced5" />

Cuando se muestran en hex ya es posible identificar

<img width="1028" height="240" alt="image" src="https://github.com/user-attachments/assets/e758442f-0d7e-4ae9-ae02-04942e880579" />

**Experimento**

Voy a quitar la línea de código que agregamos y pondré el data = "{},{},{},{}\n".format(xValue, yValue, aState,bState) para ver cómo se ve el texto y si varía.

**ASCII**

<img width="978" height="301" alt="image" src="https://github.com/user-attachments/assets/efeb5744-55cc-4bd5-adb8-42cabaf6d441" />


<img width="1042" height="266" alt="image" src="https://github.com/user-attachments/assets/7d2532f5-d0de-41ff-87a2-c584b4f9e517" />

Realizar este experimento me sirvió para comprender para qué sirve el struct.pack('>2h2B'...) que habíamos puesto al inicio de la actividad. A pesar de haber leído que hacía, el poder verlo en acción personalmente me sirve para tener más claros los conceptos. 

**Conclusión**

El '>2h2B' es una secuencia de bytes en formato binario y compacta, sirve para enviar datos entre dispositivos de forma rápida. En cambio, la línea data = "{},{},{},{}\n".format(xValue, yValue, aState, bState) genera una cadena de texto legible que muestra los valores separados por comas, lo cual es útil para ver fácilmente los datos.

Voy a poner el código de shake para analizar qué sucede. Veo que cada que se mueve el microbit se generan 6 bits. 

<img width="1028" height="297" alt="image" src="https://github.com/user-attachments/assets/7609ef31-2032-4e0f-be63-76a792fb1707" />

Esta explicación me sirvió para comprender mejor por qué son 6 bits y que significa:

2h: dos enteros de 16 bits con signo (xValue y yValue).
2B : dos enteros de 8 bits sin signo (aState y bState).

Tamaño total:
Cada h = 2 bytes → 2 x 2 = 4 bytes
Cada B = 1 byte → 2 x 1 = 2 bytes

Total: 6 bytes por mensaje

**Conclusión**

Los primeros 4 bytes corresponden a dos números enteros con signo (xValue y yValue), que representan las lecturas del acelerómetro. Los últimos 2 bytes son valores sin signo (0 o 1) que indican el estado de los botones A y B (presionado o no).

El mensaje binario se escribe como complemento a dos que es para convertirlo en un número negativo. Escribir el número positivo en binario, luego se invierten los bits y por último se le suma 1.

Para el último experimento veo como funcionan uno al lado del otro pero más arriba ya se me había ocurrido hacerlo y respondí las preguntas.

<img width="982" height="300" alt="image" src="https://github.com/user-attachments/assets/7435a429-5aab-4e5d-9bd4-cd592a9cf430" />

### Actividad 03 

En la unidad anterior teníamos que enviar información delimitada pero como el receptor ya sabe que cada paquete tiene 6 bytes, no necesita mirar comas o saltos de línea.









