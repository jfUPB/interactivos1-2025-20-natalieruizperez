# Unidad 1

## 🔎 Fase: Set + Seek

### Actividad 01

#### ¿Qué es un sistema físico interactivo?  
  Un sistema físico interactivo es un sistema mediante el cual una o más personas pueden interactuar. Estos sistemas utilizan tecnologías, como pantallas, sensores, etc, para generar estímulos que pueden ser visuales, auditivos, u otros. La interacción ocurre cuando el sistema recibe información del entorno o del usuario que se conoce como inputs. Según la información que reciba este ejecuta una acción conocida como output para crear una experiencia.

#### ¿Cómo podrías aplicar lo que has visto en tu perfil profesional?
   Creo que se podrían crear experiencias visuales en tiempo real aplicadas al modelado y animación en Blender. Por ejemplo, se podrían hacer animaciones 3D que respondan al sonido o movimiento. Además, pienso que se podrían usar simulaciones de ropa o cabello para que se vea más realistas.

### Actividad 02
#### ¿Qué es el diseño/arte generativo?
 El diseño o arte generativo consiste en crear imágenes, sonidos o productos interactivos mediante sistemas que se basan en algoritmos y reglas. En lugar de hacerlo todo manualmente, es posible crear condiciones que permiten a la máquina generar los resultados de manera autónoma o casi autónoma. Estas reglas pueden cambiarse para controlar qué tan aleatorio es para que tenga un toque más humano.
  
#### ¿Cómo podrías aplicar lo que has visto en tu perfil profesional?
   Podría aplicar el arte generativo y combinarlo con sistemas físicos interactivos para crear visuales en tiempo real que respondan a estímulos. Por ejemplo, podría crear visuales generativos en Blender que reaccionen en conciertos o presentaciones, y también me gustaría hacer presets para controlar ciertos momentos específicos, con el propósito de automatizar y hacerlo más simple. También considero que sería interesante crear ambientes con objetos 3D donde el fondo pueda cambiar mediante un algoritmo para crear diferentes estilos y así tener también variaciones y control sobre los resultados generados por el sistema.

  
   *** 
### Actvidad 03
##### Notas
Resumen de cómo conectar el micro-bit:
1. Se abre micro:bit para copiar el código.
2. Se conecta y se le da click a los tres puntos al lado de "send to micro-bit" para conectarlo
3. Una vez conectado puedo darle click a "send to micro-bit"
4. Ahora es necesario ir al editor p5js y poner el otro código.
5. Después en el index debajo de "link" se copia el código para acceder una biblioteca.
6. Luego le doy a "connect to micro:bit" y escojo el dispositivo.
***
   
#### En este sistemas físico interactivo identifica los inputs, outputs y el proceso.
#### Inputs
En este sistema físico interactivo los inputs serían los botones, lo que permite detectar el movimiiento (acelerómetro), el cable que permite conectar el microbit al pc (serial). 

#### Outputs 
los outputs serían lo que se ve en la patalla como el circulo rojo con la letra A, el circulo B amarillo, el circulo C verde, la cara y corazón del microbit.

#### Proceso
El proceso es el siguiente: Al presionar el input que es botón izquierdo del lado A, en la pantalla del computador se ve en el programa el cículo A de color rojo, el cual sería el output. En el caso de presionar el botón derecho B que es el input aparecerá en la pantalla un círculo amarillo con la letra B, el cual sería el output. También si lo agito, lo cual es el input, puedo ver en la pantalla un círculo verdce con la letra C. Finalmente si le doy click en la pantalla del computador en donde dice "send love", lo que sería el input, obtendría como output un corazón. También al conectar el micro-bit el input sería la conexión y el output la carita feliz. En conclusión, los inputs se transforman en los outputs, es posible observar que cuando el programa recibe algo, este hace una operación para que cambie algo, las cuales serían las reglas del sistema.

### Actividad 4

https://editor.p5js.org/natalieruizperez/full/A2ASIaCXc

~~~
function setup() {
  createCanvas(400, 400);
  noStroke();
}

function draw() {
  background(0,10);
  fill(random(255), random(255), random(255));
  
  t = frameCount;

  x = mouseX + cos(t) * 50;
  y = mouseY + sin(t) * 50;

  circle(x, y, 100);
}
~~~

<img width="396" height="381" alt="image" src="https://github.com/user-attachments/assets/0e84163c-dd63-40d0-86bd-3dafcccc33e4" />
<img width="386" height="384" alt="image" src="https://github.com/user-attachments/assets/af1c4022-9d19-4333-99c7-6372168ef1e8" />






 


