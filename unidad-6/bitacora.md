
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
Apraece que está escuchando la url en ese puerto 



**3. Describe lo que ves inicialmente en page1 y page2 en tu navegador.**

Inicialmente se ven dos círculos solos cada uno con una esfera 

**4. ¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?**

<img width="681" height="188" alt="image" src="https://github.com/user-attachments/assets/3adfa141-8595-4bd0-936c-a158369c7955" />

Cuando se apren aparece que un usuario se conecto y el identificador, lo mismo con la página dos. También aparece que se están recibiendo los datos. Llega loa posición en x, en y, el ancho de la ventana y la altura de la ventana.

**5. Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?**

Visualmente en ambas páginas hay dos círculos con una línea negra por la mitad, al arrastrar las ventanas se ve como esa línea se actualiza y se ve una conexión entre ambos círculos a pesar de estar en ventanas diferentes.

Las coordenadas de x son de la esquina superior izquierda

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

Si no recuerdo mal la parte de HTML es como todo el aspecto de la página entonces sería por ejemplo el fondo, la distribución de botones y el texto como dice en el ejemplo de la pregunta. La parte que es css no tengo muy clara cual sería porque se qu econ html uno también puede escoger el color de los elementos de la página y como nunca he usado css para crear una pensaría que serviría para hacer interacciones con la página. La parte que creo que es JavaScript es AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA



**6. Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”. ¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web? ¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?

   
**7. ¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor?** ¿Se te ocurre alguna ventaja para los desarrolladores?**

**8. Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?**


