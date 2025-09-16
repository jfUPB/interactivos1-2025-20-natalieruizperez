
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

**Conclusión**

Los números que ponga entre paréntesis en el uart.init son la velocidad en la que se van a mandar los bytes, por lo que en el p5js debo de poner la misma velocidad para que pueda recibir los datos correctamente.

---

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

---

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

---
### Actividad 03 

En la unidad anterior teníamos que enviar información delimitada pero como el receptor ya sabe que cada paquete tiene 6 bytes, no necesita mirar comas o saltos de línea.

<img width="1568" height="729" alt="image" src="https://github.com/user-attachments/assets/ba47bdbf-1a19-4af7-8e67-e30a129789f4" />

**Código**

```js
if (port.availableBytes() >= 6) {
    let data = port.readBytes(6);
    if (data) {
    const buffer = new Uint8Array(data).buffer;
    const view = new DataView(buffer);
    microBitX = view.getInt16(0);
    microBitY = view.getInt16(2);
    microBitAState = view.getUint8(4) === 1;
    microBitBState = view.getUint8(5) === 1;
    updateButtonStates(microBitAState, microBitBState);

    print(`microBitX: ${microBitX} microBitY: ${microBitY} microBitAState: ${microBitAState} microBitBState: ${microBitBState} \n` );

    /*
    microBitX = int(values[0]) + windowWidth / 2;
    microBitY = int(values[1]) + windowHeight / 2;
    microBitAState = values[2].toLowerCase() === "true";
    microBitBState = values[3].toLowerCase() === "true";
    updateButtonStates(microBitAState, microBitBState);
    */

    }
}


```

**Código anterior**

```js
  if (port.availableBytes() > 0) {
      let data = port.readUntil("\n");
      if (data) {
        data = data.trim();
        let values = data.split(",");
        if (values.length == 4) {
          microBitX = int(values[0]) + windowWidth / 2;
          microBitY = int(values[1]) + windowHeight / 2;
          microBitAState = values[2].toLowerCase() === "true";
          microBitBState = values[3].toLowerCase() === "true";
          updateButtonStates(microBitAState, microBitBState);
        } else {
          print("No se están recibiendo 4 datos del micro:bit");
        }

```

El código anterior trabaja con datos en formato texto que se envían como cadenas separadas por comas y terminadas con un salto de línea. En cambio, el código actual trabaja con datos binarios de 6 bytes. Por eso, el programa lee exactamente esos 6 bytes y extrae los valores directamente, lo que hace la comunicación más rápida y menos propensa a errores.

Al ejecutar el código muchas veces en la consola aparece un error. Este error se produce porque no hay una forma de saber dónde empieza cada paquete de datos. Como los datos llegan de forma continua y no tienen delimitadores, p5.js puede comenzar a leer desde cualquier byte, incluso desde la mitad de un paquete.

Esto me sirvió para entenderlo: Porque el receptor (p5.js) lee 6 bytes sin verificar si están alineados correctamente. Si los datos llegan desfasados, puede comenzar a leer desde la mitad de un paquete anterior.

Ejemplo:

  Micro:bit envía: [01 f4 02 0c 01 00][01 f4 02 0c 01 00]
  
  Pero p5.js lee desde el segundo byte: f4 02 0c 01 00 01
  
  Resultado: datos incorrectos.

Se usa el framing para evitar este tipo de errores, se le adicionó al código el framing para que funcione correctamente, en esta parte del código veo conceptos con los que no estoy familiarizada. 


```js
let serialBuffer = []; // Se agregó para acumular bytes

function readSerialData() {
  let available = port.availableBytes();
  if (available > 0) {
    let newData = port.readBytes(available);
    serialBuffer = serialBuffer.concat(newData);
  }

  while (serialBuffer.length >= 8) {
    if (serialBuffer[0] !== 0xaa) {
      serialBuffer.shift(); // Buscar el header
      continue;
    }

    if (serialBuffer.length < 8) break;

    let packet = serialBuffer.slice(0, 8);
    serialBuffer.splice(0, 8); // Remueve el paquete del buffer

    let dataBytes = packet.slice(1, 7);
    let receivedChecksum = packet[7];
    let computedChecksum = dataBytes.reduce((acc, val) => acc + val, 0) % 256;

    if (computedChecksum !== receivedChecksum) {
      console.log("Checksum error in packet");
      continue;
    }

    // Extraer datos
    let buffer = new Uint8Array(dataBytes).buffer;
    let view = new DataView(buffer);
    microBitX = view.getInt16(0);
    microBitY = view.getInt16(2);
    microBitAState = view.getUint8(4) === 1;
    microBitBState = view.getUint8(5) === 1;

    updateButtonStates(microBitAState, microBitBState);

    console.log(
      `microBitX: ${microBitX} microBitY: ${microBitY} microBitAState: ${microBitAState} microBitBState: ${microBitBState}`
    );
  }
}
```
---

**Tengo nuevas preguntas:**

**1. ¿Qué hace el serialbuffer y por qué ya no se port.readBytes?**

serialBuffer es un arreglo que acumula los bytes recibidos del puerto serial así que en vez de leer solo si hay exactamente los bytes como antes port.readBytes, se lee todo lo disponible y se guarda en un buffer, que se analiza con cuidado.

**2. ¿Cuál es la diferencia entre serialBuffer.slice y serialBuffer.splice? veo que tienen nombres similares.**

slice copia parte del arreglo; splice la elimina. Ambas se usan juntas para leer y limpiar el buffer. Esto me sirvió para entenderlo mejor: slice(0, 8) → Toma los primeros 8 bytes (sin quitarlos aún). splice(0, 8) → Elimina esos 8 bytes del serialBuffer. (porque ya se procesaron).

**3. ¿Qué es checksum y cómo funciona?**

Es un valor numérico que se calcula a partir de un conjunto de datos. Su propósito es detectar errores de transmisión. Es fundamental porque se usa para verificar que los datos recibidos son los mismos que los enviados, sin alteraciones. El emisor genera un paquete de datos, después calcula la suma de los bytes y se saca el residuo de 256 para que quepa en un byte. Ese checksum lo envía junto con el paquete y p5.js recibe el paquete, calcula su propio checksum de los datos y lo compara con el checksum recibido.

Partes del código donde aparece:

**Microbit**

```py
# Se guardan datos
data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))

checksum = sum(data) % 256

# Se construye el paquete
packet = b'\xAA' + data + bytes([checksum])

# Envia el paquete
uart.write(packet)
```

**P5.js**

```js
let dataBytes = packet.slice(1, 7); // bytes 1 a 6 del paquete
let receivedChecksum = packet[7];   // Último byte

// Se calcula checksum
let computedChecksum = dataBytes.reduce((acc, val) => acc + val, 0) % 256;

// Comparación
if (computedChecksum !== receivedChecksum) {
  console.log("Checksum error in packet");
  continue; // paquete con error, no lo usamos
}
```

**Conclusión de las preguntas**
El serial buffer es un espacio temporal donde se almacenan los datos que llegan por la comunicación serial antes de ser procesados y El checksum es un número que se calcula sumando los datos que queremos enviar para asegurarnos de que no se hayan cambiado o dañado durante el envío. Cuando enviamos información, también mandamos ese número. La persona que recibe la información calcula el número otra vez y lo compara con el que recibió. Si los dos números son iguales, significa que la información llegó bien si no, quiere decir que hubo un error y hay que enviarla de nuevo.

---
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
Al comparar el código final y el anterior se puede ver que los dos programas hacen casi lo mismo, pero el primer programa muestra en la consola los datos que llegan (como la posición y botones), mientras que el segundo no lo hace.  El segundo programa centra mejor el dibujo en la pantalla al mover las coordenadas del micro:bit al medio. Además,  Esto hace que el primero sea más útil para ver si todo está funcionando bien, y el segundo sea más limpio para solo dibujar.





