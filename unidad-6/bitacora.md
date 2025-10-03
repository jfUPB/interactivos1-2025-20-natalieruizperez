
# Evidencias de la unidad 6

---
## Actividad 01
<img width="573" height="360" alt="image" src="https://github.com/user-attachments/assets/a6de843e-8f86-42d1-8674-e68ad4647e5c" />

<img width="711" height="361" alt="image" src="https://github.com/user-attachments/assets/e3f72c30-dd5b-440b-aa9a-cf54d97094c1" />

**1. ¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito?**
<img width="356" height="75" alt="image" src="https://github.com/user-attachments/assets/01c2d85b-f814-4f35-b173-0092e7a8e953" />

Cuando puse npm install se añadieron paquetes, es decir, se instalan librerías que se necesitan y creo que su propósito es para no tener que distribuir las dependencias y así descargarlas.

**2. ¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje?**

<img width="545" height="96" alt="image" src="https://github.com/user-attachments/assets/5e0cd717-794b-4a3a-892e-3e005a012cfe" />
Aparece que está escuchando la url en ese puerto.

**3. Describe lo que ves inicialmente en page1 y page2 en tu navegador.**

Inicialmente se ven dos círculos solos cada uno con una esfera pero aunque se muevan las pestañas estas permanecen conectadas 

**4. ¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?**

<img width="681" height="188" alt="image" src="https://github.com/user-attachments/assets/3adfa141-8595-4bd0-936c-a158369c7955" />

Aparece que un usuario se conectó y el identificador, lo mismo con la página dos. También aparece que se están recibiendo los datos. Llega la posición en x, en y, el ancho de la ventana y la altura de la ventana.

**5. Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?**

Visualmente en ambas páginas hay dos círculos con una línea negra por la mitad, al arrastrar las ventanas se ve como esa línea se actualiza y se ve una conexión entre ambos círculos a pesar de estar en ventanas diferentes.

Las coordenadas de x son de la esquina superior izquierda.

---
## Actividad 02

**1. Piensa en cómo te conectas a Internet en casa o en la Universidad. ¿Usas Wi-Fi? ¿Un cable de red? Eso es simplemente tu “rampa de acceso” a la gran red de carreteras. ¿Qué pasaría si esa rampa se corta? Anota tus ideas.**

En mi casa uso wifi, si esa rampa se corta entonces ya no sería posible que haya una conexión entre el computador y otros computadores. Esta conexión es la ue permite que al enviar un mensaje a otra persona en otra parte del mundo le pueda llegar a pesar de estar conectados en redes diferentes.

**2. ¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria (no necesariamente digitales)? Por ejemplo, al pedir comida en un restaurante. ¿Quién es el cliente y quién el servidor? ¿Qué se pide y qué se entrega?**

Al pedir comida en un restaurante el cliente es la persona que va a pedir comida y el servidor es el restaurante porque es el que da comida, esta comida es la misma que pide el cliente y la que entrega el restaurante. Otra relación cliente sevidor es en las comisiones, un artista da su servicio que puede ser hacer un dibujo o un modelo 3d y el cliente lo recibe.

**3. Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor?**

Mi página favorita es https://www.friv.com/, creo que si no escribo la ruta específica de todas formas me lleva a la dirección correcta porque cuando me pongo a pensar nunca la escribo.

**4. Compara HTTP con los protocolos seriales que usaste. ¿Qué similitudes encuentras? ¿Qué diferencias clave ves? ¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?**

Al comparar los diferentes protocolos entre las similitudes que encuentro está que ambos sirven para interpretar el texto o comandos que le escribe el usuario en otro lenguaje por así decirlo y le devuelve. En las diferencias clave, lo que veo es que por ejemplo en el protocolo ASCII los datos se envían de forma más simple y directa. En cambio http es mucho más complejo, yo he programado páginas en html y es muy confuso. Esto es porque se usa para la comunicación a través de Internet. 

**5. Piensa en una página web simple, como un formulario de login. ¿Qué parte crees que es HTML (ej. los campos de texto, el botón)? ¿Qué parte es CSS (ej. el color del botón, el tipo de letra)? ¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?**

En una página simple como un formulario de login, el HTML es lo que crea los campos y botones. El CSS cambia cómo se ve todo el aspecto de la página, los colores y las letras. Y el JavaScript es lo que hace que la página reaccione, como revisar si se llena algo o mostrar mensajes sin recargar.

**6. Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”. ¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web? ¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?

El draw() de p5.js siempre está dibujando aunque no pase nada nuevo. En cambio, el modelo basado en eventos solo  funciona cuando pasa algo, entonces es más eficiente porque no hace trabajo de más y la página va más rápido.
   
**7. ¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor?** ¿Se te ocurre alguna ventaja para los desarrolladores?**

Usar JavaScript en cliente y servidor es bueno porque asi solo es necesario saber un lenguaje y seria mas fácil de hacer. También se puede compartir código entre cliente y servidor, entonces no hay que repetir mucho trabajo.

**8. Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?**

HTTP es cuando tú preguntas algo y el servidor te responde, pero después se corta la conexión. WebSockets es como tener una llamada y dos pueden hablar sin parar. Esto sirve para cosas que necesitan funcionar en tiempo real, como juegos, chats o apps.

## Activad 03

**1. Detuve el servidor, después cambié la primera ruta de /page1 a /pagina_uno e inicié el servidor.**

<img width="433" height="199" alt="image" src="https://github.com/user-attachments/assets/56d8b218-0b9b-4e2a-b6a1-0ee707d98e7d" />

Intento de acceder a  http://localhost:3000/page1, la página ya no funciona.

<img width="654" height="370" alt="image" src="https://github.com/user-attachments/assets/76a14021-2890-42be-befb-890d90d21690" />


Al acceder a http://localhost:3000/pagina_uno la página ya funciona, esto me dice que el servidor responde a las URLs del código y cada ruta está asociada a una respuesta. Cuando cambio la ruta en el código,tengo que usar esa porque el servidor solo responde a las rutas que tiene configuradas.

<img width="1427" height="902" alt="image" src="https://github.com/user-attachments/assets/76ca72b1-80b1-4160-99f8-89207ec1e32e" />


---

**Abre http://localhost:3000/page1 en una pestaña. Observa la terminal del servidor. ¿Qué mensaje ves? Anota el ID.**

A user connected - ID: d5X40J7eJ3OiMhRyAAAD


**Abre http://localhost:3000/page2 en OTRA pestaña. Observa la terminal. ¿Qué mensaje ves? ¿El ID es diferente?**

A user connected - ID: BzlnyVgVfJHLhFisAAAB

**Cierra la pestaña de page1. Observa la terminal. ¿Qué mensaje ves? ¿Coincide el ID con el que anotaste?**

User disconnected - ID: d5X40J7eJ3OiMhRyAAAD

**Cierra la pestaña de page2. Observa la terminal.**

User disconnected - ID: BzlnyVgVfJHLhFisAAAB

**Evidencia**

<img width="440" height="206" alt="image" src="https://github.com/user-attachments/assets/2eeb98eb-f783-44d1-ae92-340eca2b291d" />

---

Inicia el servidor y abre page1 y page2.

Mueve la ventana de page1. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves?

<img width="437" height="227" alt="image" src="https://github.com/user-attachments/assets/c1114e1b-2818-4988-8966-05d541ac1df8" />

El evento que se registra es que hubo una actualización y manda valores de x, y, el ancho y la altura. También se ve la información de clientes conectados, el status y la actualización que recibe.

**Mueve la ventana de page2. Observa la terminal. ¿Qué evento se registra ahora? ¿Qué datos ves?**

También se ven los mismos datos solo que esta vez se registra win2update en lugar de win1update.

<img width="442" height="242" alt="image" src="https://github.com/user-attachments/assets/21347faf-f893-4bf4-9b40-56a633995ce7" />

**Experimento clave: cambia socket.broadcast.emit(‘getdata’, page1); por socket.emit(‘getdata’, page1); (quitando broadcast). Reinicia el servidor, abre ambas páginas. Mueve page1. ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no? (Pista: ¿A quién le envía el mensaje socket.emit?). Restaura el código a broadcast.emit.**

<img width="921" height="242" alt="image" src="https://github.com/user-attachments/assets/4f75c0f7-9949-4407-a781-ac699baea6f0" />

Al mover la page1 no se actualiza la page 2, pero al mover la page 2 si se actualiza la uno, esto es porque el socket.emit le envía el mensaje desde la página 1 a la 2 pero no modifiqué la línea de código donde se envía la información desde la página 2.

<img width="490" height="123" alt="image" src="https://github.com/user-attachments/assets/30a13327-2245-48b5-879a-bacd467b9f5a" />

---
**Detuve el servidor, cambié const port = 3000; a const port = 3001; e inicié el servidor. ¿Qué mensaje ves en la consola? ¿En qué puerto dice que está escuchando?**

Ahora aparece que el puerto que está escuchando es el 3001.

<img width="360" height="44" alt="image" src="https://github.com/user-attachments/assets/af053023-81b5-4e7b-b3ad-e874c97cb3dd" />

**Intenta abrir http://localhost:3000/page1. ¿Funciona?**

<img width="1196" height="898" alt="image" src="https://github.com/user-attachments/assets/4d4d23ae-fa76-4059-92db-e8eea5d378c6" />


**Intenta abrir http://localhost:3001/page1. ¿Funciona?**

<img width="661" height="312" alt="image" src="https://github.com/user-attachments/assets/3b15ec09-7caf-4c3c-838f-80003bcd0a33" />


**¿Qué aprendiste sobre la variable port y la función listen? Restaura el puerto a 3000.**

Al cambiar los valores de const modifico el puerto y cuando inicio el servidor, la terminal muestra el mensaje de que el servidor está escuchando 3001. Cuando abro http://localhost:3000/page1, no funciona porque el servidor ya no esta en ese puerto pero al usar http://localhost:3001/page1, sí funciona. En conclusión la variable port define en qué puerto escucha el servidor, y la función listen() usa esa variable para activarse.

---

## Actividad 04

Abrí page2.html con el servidor corriendo y aprete f12 para abrir la consola de desarrollador, después detuve el servidor Detén el servidor Node.js (Ctrl+C) y refresque la página page2.html. **¿Ves algún error relacionado con la conexión? ¿Qué indica?**

<img width="392" height="431" alt="image" src="https://github.com/user-attachments/assets/3abbd256-cb43-4906-906e-4aa6c4b55d43" />

El error indica que se quiere concectar pero la URL no existe, es necesario abrir la página a tra´ves del servidor para que funcione correctamente.

**Vuelve a iniciar el servidor y refresca la página. ¿Desaparecen los errores?**

Si desaparecen por un momento antes de que intente conectarse.

<img width="400" height="442" alt="image" src="https://github.com/user-attachments/assets/f9e8ec1d-eded-4323-9fcf-ba1f8c9876ec" />

---

Comenta la línea socket.emit(‘win2update’, currentPageData, socket.id); dentro del listener connect. Reinicia el servidor y refresca page1.html y page2.html. Mueve la ventana de page2 un poco para que envíe una actualización.

**¿Qué pasó? ¿Por qué?**


---

**Abre ambas páginas (es posible que ya las tengas abiertas). Mueve la ventana de page1. Observa la consola del navegador de page2. ¿Qué datos muestra?**

<img width="881" height="485" alt="image" src="https://github.com/user-attachments/assets/9ac15d37-49ce-4bbb-b544-23070a0d5e8b" />

Se muestran los datos de sincronización y page 2 recibe valores de x, y , altura y ancho desde la page1.

**Mueve la ventana de page2. Observa la consola de page1. ¿Qué pasa? ¿Por qué?**

Pasa lo mismo, los valores se actualizan, esto pasa porque el servidor está revisando constantemente que cambios hay entre las ods páginas para actualizarlo, el cambio se hace en la page uno porque es el receptor de lo que haga la page 2.

---

**Observa checkWindowPosition() en page2.js y modifica el código del if para comprobar si el código dentreo de este se ejecuta.**
Mueve cada ventana y observa las consolas.

  Página 1

<img width="1777" height="978" alt="image" src="https://github.com/user-attachments/assets/9f2cc957-5d72-4b0f-8449-e0ce5ea128e6" />


  Página 2
<img width="885" height="483" alt="image" src="https://github.com/user-attachments/assets/35db86e6-acde-4631-8f49-d64e88546514" />

**¿Qué puedes concluir y por qué?**

Modifiqué la función checkWindowPosition() en page2.js que aparezca un mensaje cuando sucede el if. Al mover la ventana, el mensaje apareció y eso confirma que el if detecta correctamente los cambios en posición o tamaño de la ventana. En page1.js no salió el mensaje porque modifique el script.

---

Cambia el background(220) para que dependa de la distancia entre las ventanas. Puedes calcular la magnitud del resultingVector usando let distancia = resultingVector.mag(); y luego usa map() para convertir esa distancia a un valor de gris o color. background(map(distancia, 0, 1000, 255, 0)); (ajusta el rango 0-1000 según sea necesario).

```js
function draw() {
    let vector1 = createVector(currentPageData.x, currentPageData.y);
    let vector2 = createVector(remotePageData.x, remotePageData.y);
    let resultingVector = createVector(vector2.x - vector1.x, vector2.y - vector1.y);
    
    let distancia = resultingVector.mag();
    let gris = map(distancia, 0, 1000, 255, 0);
    background(gris); // cambia el fondo según la distancia

    if (!isConnected) {
        showStatus('Conectando al servidor...', color(255, 165, 0));
        return;
    }
    
    if (!hasRemoteData) {
        showStatus('Esperando conexión de la otra ventana...', color(255, 165, 0));
        return;
    }
    
    if (!isFullySynced) {
        showStatus('Sincronizando datos...', color(255, 165, 0));
        return;
    }

    // Solo dibujar cuando esté completamente sincronizado
    drawCircle(point1[0], point1[1]);
    checkWindowPosition();

    stroke(50);
    strokeWeight(20);
    drawCircle(resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
    line(point1[0], point1[1], resultingVector.x + remotePageData.width / 2, resultingVector.y + remotePageData.height / 2);
}
```

Si están más lejos se pone más oscuro.

<img width="1791" height="995" alt="image" src="https://github.com/user-attachments/assets/75233512-3513-45f9-9376-edefc5cc5365" />

Mientras más cerca, más claros.

<img width="1802" height="985" alt="image" src="https://github.com/user-attachments/assets/b8c405fa-d26c-4135-bd09-aff4a1f24b2b" />

**Inventa otra modificación creativa.**

Ahora mientras más lejos estén la bola se vuelve más grande.

<img width="1772" height="871" alt="image" src="https://github.com/user-attachments/assets/357a4e30-2751-45ec-b357-46f67364d7a5" />


```js
function drawCircle(x, y) {
    let distancia = dist(currentPageData.x, currentPageData.y, remotePageData.x, remotePageData.y);
    let size = map(distancia, 0, 1000, 100, 300); // Tamaño cambia de 100 (cerca) a 300 (lejos)
    fill(255, 0, 0);
    ellipse(x, y, size, size);
}
```

---

## Actividad 05

Con el ejercico anterior se me ocurrió hacer un código en el que el círculo sea una especie de globo y al mover la otra pestaña este se va a ir inflando cada vez que la ventana se acerque al círculo haciendo que explote cuando llegue a un tamaño determinado.

---

## Nota 3.0


-Actividad 01: Completa (0.5)

-Activida 02:  Completa (0.5)

-Actividad 03: Completa (1.0)

-Actividad 04: Completa (1.0)

-Activida 05:  Incompleta (0)




