
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

**4. Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).**

<img width="1828" height="899" alt="image" src="https://github.com/user-attachments/assets/95e145ba-eda4-4eed-88c5-0c092310bafd" />

<img width="1322" height="897" alt="image" src="https://github.com/user-attachments/assets/28a05c45-6d82-4057-9bfd-dd87f2113fd7" />

![WhatsApp Image 2025-10-16 at 4 53 54 PM](https://github.com/user-attachments/assets/92f74189-392e-40d9-b4b4-e9ffef6c9d0d)

![WhatsApp Image 2025-10-16 at 4 53 54 PM (1)](https://github.com/user-attachments/assets/c8e6b79c-1f6e-43ed-8057-21eaa9ab73ff)


---
## Actividad 03

**1. ¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?**

AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

**2. Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso?**

El evento touchMoved() detecta el movimiento del dedo en el celular, y socket.emit envia el mensaje y lo recibe el socket.on, con console.log lo muestra en gitbash y el socket.broadcast.emit hace que le llegue el mensaje a todos menos al celular que se encarga de mandar el mensaje. Se usa socket.broadcast.emit para que el celular no se envié a si mismo el mensaje.

**3. Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué?**

El mensaje lo recibirían las dos computadoras porque el que emite el mensaje es el celular y quién lo recibe el computador por el socket.broadcast.emit que le manda a todos menos al que envía mensajes.

**4. ¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución?**

Permite saber qué está sucediendo y qué líneas de código se están ejecutando correctamente, el consele.log también lo uso cuando preogramo en unity y es muy útil para saber qué está pasando y también cuál información recibe el programa. En este código informa sobre si se conectaron o desconectaron los clientes para que uno pueda saber si está funcionando, además también muestra las coordenadas.

---
## Actividad 04

**Realiza un diagrama donde muestres el flujo completo de datos y eventos entre los tres componentes: móvil, servidor y escritorio. Puedes ilustrar con un ejemplo de coordenadas táctiles (x, y) y cómo viajan a través del sistema..**

<img width="936" height="612" alt="image" src="https://github.com/user-attachments/assets/dc82ba76-98e0-4326-8a4d-211a645ad343" />


---
## Actividad 05

**Diseña una aplicación interactiva que use el touch del móvil para controlar una visuales de tema musical de tu elección. Las visuales correrán en una aplicación de escritorio (desktop). Recuerda que ambas aplicaciones las construirás usando p5.js y utilizando el servidor Node.js como puente. Implementa tu diseño. Puedes usar IA generativa para ayudarte a escribir el código, pero primero debes hacer el diseño de lo que quieres.
Incluye todos los códigos (servidor y clientes) en tu bitácora.**

Escogí amsterdam de nothing but thieves que es una de mis canciones favoritas. Al pensar en una visual y teniendo en cuenta el código base que eran círculos se me ocurrío que fueran círculos de colores que crecieran cada vez que subiera el volumen de la canción. Esos círculos son de diferentes colores pero cuando se toca dos veces la pantalla con el dedo se ponen rojos y explotan. Si se lleva el dedo hacia arriba se mueven hacia esa dirección y lo mismo si se va para abajo y para un lado.

**server**
```js
// server.js

const express = require('express');
const http = require('http');
const socketIO = require('socket.io');

const app = express();
const server = http.createServer(app);
const io = socketIO(server);
const port = 3000;

// Sirve los archivos estáticos desde la carpeta 'public'
app.use(express.static('public'));

io.on('connection', (socket) => {
    console.log('New client connected');
    
    // El servidor retransmite el mensaje (touch o explosion) a todos los demás clientes
    socket.on('message', (message) => {
        // Usa socket.broadcast.emit para enviar a todos EXCEPTO al remitente (el móvil)
        socket.broadcast.emit('message', message);
    });

    socket.on('disconnect', () => {
        console.log('Client disconnected');
    });
});

server.listen(port, () => {
    console.log(`Server is listening on http://localhost:${port}`);
    console.log(`Desktop client: http://localhost:${port}/desktop/index.html`);
    console.log(`Mobile client: http://localhost:${port}/mobile/index.html`);
});
```

**sketch mobile**

```js
// public/mobile/sketch.js

let socket;
let lastTouchX = null;
let lastTouchY = null;
const threshold = 5; 

// Variables para el doble toque
let lastTapTime = 0;
const doubleTapDelay = 300; // Máximo 300ms entre toques

function setup() {
    createCanvas(300, 400); 
    background(220);
    socket = io();

    socket.on('connect', () => {
        console.log('Connected to server');
    });

    socket.on('disconnect', () => {
        console.log('Disconnected from server');
    });
}

function draw() {
    background(220);
    fill(50);
    textAlign(CENTER, CENTER);
    textSize(18);
    text('Arrastra para color y movimiento', width / 2, height / 2 - 20);
    text('DOBLE TOQUE para EXPLOSIÓN 💥', width / 2, height / 2 + 10);
    textSize(12);
    text(`(X: ${lastTouchX ? lastTouchX.toFixed(0) : '—'}, Y: ${lastTouchY ? lastTouchY.toFixed(0) : '—'})`, width / 2, height / 2 + 40);
}

// touchStarted es necesario para que touchMoved/touchEnded funcionen bien en navegadores móviles
function touchStarted() {
    return true; 
}

// **NUEVA LÓGICA:** GESTIÓN DEL DOBLE TOQUE
function touchEnded() {
    let currentTime = millis();
    
    if (currentTime - lastTapTime < doubleTapDelay) {
        // DOBLE TOQUE DETECTADO
        if (socket && socket.connected) {
            let explosionData = {
                type: 'double_tap_explosion', 
                timestamp: Date.now()
            };
            socket.emit('message', explosionData);
            console.log('Double Tap Explosion signal sent!');
            
            lastTapTime = 0; // Reinicia el temporizador
        }
    } else {
        // Primer toque, guarda el tiempo
        lastTapTime = currentTime;
    }
    
    return false;
}

// Envía la posición del arrastre para el control de color y movimiento
function touchMoved() {
    if (socket && socket.connected) {
        let dx = abs(mouseX - lastTouchX);
        let dy = abs(mouseY - lastTouchY);

        // Envía el evento 'touch' solo si hay movimiento
        if (dx > threshold || dy > threshold || lastTouchX === null) {
            let touchData = {
                type: 'touch',
                x: mouseX, 
                y: mouseY  
            };
            socket.emit('message', touchData);

            lastTouchX = mouseX;
            lastTouchY = mouseY;
        }
    }
    return false; // Bloquea el scroll del navegador
}
```

**sketch desktop**
```js
// public/desktop/sketch.js

let socket;
let circleX = 400; 
let circleY = 300;
let song;
let amp; // Objeto p5.Amplitude para medir el volumen
let circles = []; 
const maxCircles = 50; 
const mobileWidth = 300; 
const mobileHeight = 400; 
let currentHue = 0; 
let audioStarted = false; 

// Variables para la Explosión (Doble Toque)
let isExploding = false; 
let explosionStartTime = 0;
const explosionDuration = 500; // 500ms para el efecto completo

// Variables para el Empuje Global (Movimiento)
let movementForceX = 0;
let movementForceY = 0;
const damping = 0.93; // Fricción

// --- CLASE PARA CADA CÍRCULO EN PANTALLA ---
class AmplitudeCircle {
    constructor(x, y, initialRadius, hue) {
        this.x = x;
        this.y = y;
        this.baseR = initialRadius; 
        this.radius = initialRadius;
        this.hue = hue; 
        this.opacity = 255;
    }

    update(volumeLevel) {
        // 1. Pulsación por volumen (solo si NO está explotando)
        // Aseguramos que el radio se base en el volumen SOLO si no estamos explotando.
        // Si estamos explotando, el tamaño lo controla la lógica de explosión.
        if (!isExploding) {
            this.radius = this.baseR + volumeLevel * 100; 
        }
        
        this.opacity -= 1.0; 

        // 2. Efecto de palpitación de color
        if (circles.length >= maxCircles * 0.8) {
             this.hue = (this.hue + 2) % 360; 
        }

        // 3. LÓGICA DE MOVIMIENTO GLOBAL
        this.x += movementForceX;
        this.y += movementForceY;

        // 4. LÓGICA DE EXPLOSIÓN (Doble Toque)
        if (isExploding) {
            let elapsedTime = millis() - explosionStartTime;
            let ratio = elapsedTime / explosionDuration; // Valor de 0.0 a 1.0

            if (ratio < 1) {
                // Durante los 500ms: se pone rojo y crece notablemente
                this.hue = 0; // Tono 0 es ROJO
                
                // Crecimiento "BASTANTE GRANDE": De this.baseR a this.baseR * 4 (o más si quieres)
                // Esto hará que el radio final sea 4 veces el radio inicial del círculo.
                let targetRadius = this.baseR * 4; // <--- ¡AQUÍ ESTÁ EL CAMBIO CLAVE!
                
                // Usamos map() para interpolar el tamaño basándonos en el tiempo (ratio)
                this.radius = map(ratio, 0, 1, this.baseR, targetRadius); 
                
            } else {
                // Después de los 500ms: desaparece (Explota)
                this.opacity = 0; 
            }
        }
    }

    display() {
        colorMode(HSB, 360, 100, 100, 255);
        fill(this.hue, 80, 100, this.opacity);
        noStroke();
        ellipse(this.x, this.y, this.radius * 2);
    }
}
// ----------------------------------------------------

// --- Precarga: Carga el archivo de audio ---
function preload() {
    song = loadSound('../assets/amsterdam.mp3', 
        () => console.log('Audio file loaded successfully.'), 
        (err) => console.error('Error loading audio:', err)
    );
}

// --- Setup: Inicialización y Conexión ---
function setup() {
    createCanvas(800, 600); 
    colorMode(RGB, 255);
    background(20); 

    socket = io(); 
    
    // Lógica de Socket.IO
    socket.on('message', (data) => {
        if (data && data.type === 'touch') {
            // Empuje y color por ARRASTRE
            circleX = map(data.x, 0, mobileWidth, 0, width);
            circleY = map(data.y, 0, mobileHeight, 0, height);
            currentHue = map(data.x, 0, mobileWidth, 0, 360);
            
            movementForceX = map(data.x, 0, mobileWidth, -5, 5); 
            movementForceY = map(data.y, 0, mobileHeight, -5, 5); 

        } else if (data && data.type === 'double_tap_explosion') {
            // Activa la explosión al recibir el DOBLE TOQUE
            isExploding = true;
            explosionStartTime = millis(); 
            console.log('Double Tap Explosion triggered!'); 
        }
    });    
}

// --- Draw: Bucle de Dibujo ---
function draw() {
    colorMode(RGB, 255); 
    background(20, 20); 

    // Finaliza el estado de explosión
    if (isExploding && millis() > explosionStartTime + explosionDuration) {
        isExploding = false;
        console.log('Explosion finished.');
    }

    if (audioStarted) {
        // Aplicar la fricción (damping) al movimiento
        movementForceX *= damping;
        movementForceY *= damping;
        if (abs(movementForceX) < 0.1) movementForceX = 0;
        if (abs(movementForceY) < 0.1) movementForceY = 0;

        // Análisis de Audio
        let volume = amp.getLevel(); 
        
        // Creación de Círculos
        if (volume > 0.05 && frameCount % 3 === 0 && !isExploding) { 
            let newCircleX = random(width);
            let newCircleY = random(height);
            let initialRadius = 10 + volume * 70; 
            let hueToUse = currentHue > 0 ? currentHue : random(360); 

            let newCircle = new AmplitudeCircle(newCircleX, newCircleY, initialRadius, hueToUse);
            circles.push(newCircle);
        }
        
        // Dibujar y Actualizar Círculos
        if (circles.length > maxCircles) {
            circles.splice(0, circles.length - maxCircles);
        }

        for (let i = circles.length - 1; i >= 0; i--) {
            let circle = circles[i];
            
            circle.update(volume); 
            circle.display();

            // Eliminar si la opacidad es cero o si se sale de la pantalla por el empuje
            if (circle.opacity < 0 || circle.x < -100 || circle.x > width + 100 || circle.y < -100 || circle.y > height + 100) {
                circles.splice(i, 1);
            }
        }
    }
    
    // Mostrar estado
    colorMode(RGB, 255); 
    fill(255);
    textSize(14);
    textAlign(LEFT, TOP);
    let status = song && song.isLoaded() ? (song.isPlaying() ? 'Playing 🎧' : 'Paused/Click to Play 🖱️') : 'Loading...';
    text(`Song Status: ${status} | Círculos: ${circles.length}/${maxCircles}`, 10, 10);
    text(`Empuje (X, Y): ${movementForceX.toFixed(1)}, ${movementForceY.toFixed(1)}`, 10, 30);
    
    // Instrucción de inicio
    if (!audioStarted) {
        fill(255, 255, 0); 
        textSize(30);
        textAlign(CENTER, CENTER);
        text('CLICK PARA EMPEZAR LA MÚSICA Y LAS VISUALES', width / 2, height / 2);
    }
}

// --- Iniciar Audio al Click ---
function mouseClicked() {
    if (song && song.isLoaded() && !audioStarted) {
        song.loop();
        amp = new p5.Amplitude(); 
        amp.setInput(song);
        audioStarted = true;
    }
    return false;
}
```

**Index mobile**
```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <title>Control de Amsterdam (Móvil)</title>
    
    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
    <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
    
    <script src="sketch.js"></script>
    
    <style>
        body {
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #f0f0f0;
        }
    </style>
</head>
<body>
</body>
</html>
```

**Index desktop**
```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Visuales de Amsterdam (Desktop)</title>
    
    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
    
    <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/addons/p5.sound.min.js"></script>
    
    <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
    
    <script src="sketch.js"></script>
    
    <style>
        /* Estilos básicos para la presentación */
        body {
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #000;
            overflow: hidden;
        }
    </style>
</head>
<body>
    </body>
</html>
```

---
Rúbrica

5: realicé las 5 actividades completas y la autoevaluación.
3: realicé 4 actividades completas y la autoevaluación.
2: realicé 3 actividades completas y la autoevaluación.
1: realicé 2 actividades completas y la autoevaluación.
0.5: realicé 1 actividad completa y la autoevaluación.
0: no realicé ninguna actividad o no realicé la autoevaluación.

---
## Nota: 5.0

-Actividad 01: Completa (0.5)
-Actividad 02: Completa (0.5)
-Actividad 03: Completa (1.0)
-Actividad 04: Completa (1.0)
-Actividad 05: Completa (1.0)











