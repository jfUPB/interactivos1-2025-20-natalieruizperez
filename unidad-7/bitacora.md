
# Evidencias de la unidad 7

## Acividad 01
**1. ¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?**

Porque es local osea del propio dispositivo y para que se conecten tiene que ser una que tengan en comúm

**2. Describe brevemente qué hace npm install y npm start.**

El npm install se encarga de añadir los paquetes, instala el express y socket.io mientas qué el start hace que se inicie el servidor y la aplicación haciendo que la URL funcione correctamente.

<img width="582" height="361" alt="image" src="https://github.com/user-attachments/assets/671b09b1-1567-4ca1-b2bf-9aab2775bbbe" />

**3. ¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?**
Observo mensajes que decían que hay nuevos clientes conectados, supongo que uno era el computador y el otro el celular. También se ven las coordenadas de x y y.

<img width="726" height="432" alt="image" src="https://github.com/user-attachments/assets/5c8893f0-7c94-47da-a5aa-a368447196ab" />

**4. Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?**

Funcionó la interacción pero hay un retraso, al mover el dedo la bola roja se demora unos milisegundos y el movimiento no se ve suave, a pesar de eso funciona correctamente.

---
## Actividad 02

**1. Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?**

  Dev Tunnels es necesario en este escenario porque lo que hace es crear una conexión entre el computador y el celular. Si no se usase al copiar el URL del computador en el celular no habría sincronizacion. Esto es debido a que el local accede precisamente al dispositivo en el que se pone esa URL. El Dev Tunnels conceptualmente funciona como un intermediario y lo que hace es redireccionar la conexión.

**2. Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.**

La función touchMoved() cada vez que uno mueve el dedo, detecta ese movimiento y puede manda datos. La variable threshold se usar para solo mandar la información importante, no cada evento pequeño que pase.

**3. Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?**

La IP local funciona cuando ambos están conectados a la misma red, en cambio Dev Tunnels se usa para crear un lugar público que no depende de la red. En cuanto a desventajas la verdad ambas me parecen muy inseguras y tengo el concepto de que sería muy fácil para otras personas acceder a ellas. En ventajas está que Dev Tunnels se puede usar independientmente de la red y la de la IP local qu no se necesita internet, me hace pensar en los juegos de celular que me gustaban de pequeña que se podían jugar de forma multijugador siempre y cuando uno estuviese cerca de la otra persona y lo mejor era que se podía usar sin internet.

---

**4. Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).**

<img width="1828" height="899" alt="image" src="https://github.com/user-attachments/assets/95e145ba-eda4-4eed-88c5-0c092310bafd" />

<img width="1322" height="897" alt="image" src="https://github.com/user-attachments/assets/28a05c45-6d82-4057-9bfd-dd87f2113fd7" />

![WhatsApp Image 2025-10-16 at 4 53 54 PM](https://github.com/user-attachments/assets/92f74189-392e-40d9-b4b4-e9ffef6c9d0d)

![WhatsApp Image 2025-10-16 at 4 53 54 PM (1)](https://github.com/user-attachments/assets/c8e6b79c-1f6e-43ed-8057-21eaa9ab73ff)


---
## Actividad 03

**1. ¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?**

**2. Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso?**

El evento touchMoved() lo envía desde el celular, el evento que lo envía es el socket.broadcast.emit y lo recibe el socket.emit que se encarga de mandarlo.


socket.emit solo le manda al cliente que lo envió (no sirve acá).

io.emit le manda a todos, incluyendo al que lo mandó (no lo queremos porque el móvil ya tiene la info).

socket.broadcast.emit le manda a todos menos al emisor, que es justo lo que queremos en este cas

**3. Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué?**

El mensaje lo recibirían las dos computadoras porque el que emite el mensaje es el celular y quién lo recibe el computador por el socket.broadcast.emit que le manda a todos menos al que envía mensajes.

**4. ¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución?**

Permite saber qué está sucediendo y qué líneas de código se están ejecutando correctamente, el consele.log también lo uso cuando preogramo en unity y es muy útil para saber qué está pasando y también cuál información recibe el programa. En este código informa sobre si se conectaron o desconectaron los clientes para que uno pueda saber si está funcionando, además también muestra las coordenadas.

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

-Actividad 01: Completa (0.5)
-Actividad 02: Completa (0.5)
-Actividad 03: Completa (1.0)







