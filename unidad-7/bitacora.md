
# Evidencias de la unidad 7

## Acividad 01
**1. ¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?**


Describe brevemente qué hace npm install y npm start.

**2. El npm install se encarga de añadir los paquetes, instala el express y socket.io mientas qué el start hace que se inicie el servidor y la aplicación haciendo que la URL funcione correctamente.**

<img width="582" height="361" alt="image" src="https://github.com/user-attachments/assets/671b09b1-1567-4ca1-b2bf-9aab2775bbbe" />


**3. ¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?**

**4. Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?**

---
## Actividad 02

**1. Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?**

  Dev Tunnels es necesario en este escenario porque lo que hace es crear una conexión entre el computador y el celular. Si no se usase al copiar el URL del computador en el celular no habría sincronizacion. Esto es debido a que el local accede precisamente al dispositivo en el que se pone esa URL. El Dev Tunnels conceptualmente funciona como un intermediario y lo que hace es redireccionar la conexión.

**2. Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.**

La función touch move funciona cuando se toca la pantalla y lo que hace es que manda un bloque de código para que se ejecute al tocar la pantalla. S eusa la variable threshold en el cliente movil para que...EEEEEEEEEEEEEEE 

**3. Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?**

AAAAAAAAAAAAAAAAAAAA
---

**4. Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).**

---
## Actividad 03

**1. ¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?**

**2. Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso?**

**3. Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué?**

**4. ¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución?**

---
## Actividad 04

**Realiza un diagrama donde muestres el flujo completo de datos y eventos entre los tres componentes: móvil, servidor y escritorio. Puedes ilustrar con un ejemplo de coordenadas táctiles (x, y) y cómo viajan a través del sistema..**

---
## Actividad 05

**Diseña una aplicación interactiva que use el touch del móvil para controlar una visuales de tema musical de tu elección. Las visuales correrán en una aplicación de escritorio (desktop). Recuerda que ambas aplicaciones las construirás usando p5.js y utilizando el servidor Node.js como puente. Implementa tu diseño. Puedes usar IA generativa para ayudarte a escribir el código, pero primero debes hacer el diseño de lo que quieres.
Incluye todos los códigos (servidor y clientes) en tu bitácora.**

---
Rúbrica

5: realicé las 5 actividades completas y la autoevaluación.
3: realicé 4 actividades completas y la autoevaluación.
2: realicé 3 actividades completas y la autoevaluación.
1: realicé 2 actividades completas y la autoevaluación.
0.5: realicé 1 actividad completa y la autoevaluación.
0: no realicé ninguna actividad o no realicé la autoevaluación.

---
## Nota:






