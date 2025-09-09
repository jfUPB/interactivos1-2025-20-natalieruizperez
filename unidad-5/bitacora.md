
# Evidencias de la unidad 5

**1. Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?**
Se comunican a través del uart.write y la librerá de p5.js. Los datos que envía son xValue, yValue, aState y bState

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
