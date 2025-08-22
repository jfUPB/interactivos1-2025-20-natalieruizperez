# Unidad 3


## 🤔 Fase: Reflect

### Actividad 08 - Autoevaluación

#### Parte 1: recuperación de conocimiento (Retrieval Practice)

**1. Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?**

Una máquina de estados es aquella que permite cambiar entre acciones. Los cuatro componentes fundamentales de esta unidad son los estado, eventos, acciones y vectores de prueba.


**2. Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender varios eventos y tareas “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit o en p5.js. ¿Qué problema soluciona en comparación con usar funciones como sleep()?**

El sleep soluciona el problema de una posible saturación al enviar muchos mensajes en un mismo tiempo. La concurriencia es útil a la hora de manejar una máquina de estados porque permite que sucedna varias accines al mismo tiempo.


**3. Imagina que tienes que añadir una nueva funcionalidad a la bomba: si se recibe un evento especial (por ejemplo, una combinación de botones o un comando serial) mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?**

Lo agregaría en

**4. Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.**

Un vector de prueba es crucial para verificar que la máquina de estados funciona porque nos permite desglosar lo que se sxupne que debería de suceder. Al seguir esta forma de trabajo es más sencillo ver donde hay errores y verificar si el programa funciona correctamente.


#### Parte 2: reflexión sobre tu proceso (Metacognición)

**1. ¿Qué parte del diseño de la bomba te resultó más desafiante: crear el diagrama de estados o traducir ese diagrama a código? ¿Por qué?**

El código para p5js y microbit porque no habíamos hecho antes un programa que permitiera manejar ambos por lo que había que pensar en cómo abordarlo.

**2. Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?**

En la actividad 7 encontraba que había un error, luego de verificar que todo esuviese bien escrito me di cuenta que era porque no había puesto en el index de 05js la biblioteca para la conexión del puerto serial.

**3. El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?**

Lo que hice primero fue identificar los eventos, acciones y estados. Como ya tenía el diagrama de la unidad de la clase pasada y el código de la bomba no cambiaba significativamente me guié por este.

**4. Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?**

Sería super útil a la hora de programar los comportamientos de un jefe para un videojuego en unity. En taller 2 usé una máquina de estados para eso pero en su momento no sabía a profundidad que era lo que sucedía. Además de esto me parece que se prestaría para muchas cosas más.



### Actividad 09 - Feedback

**1. Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?**

Cuando hicimos el diagrama en el que desglosabamos el código y lo que debía de pasar, me ayudó a entender bien el funcionamiento de las acciones, estados, eventos y vectores de prueba.


**Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso? ¿Qué cambiarías o eliminarías?**

No la verdad, me enredé un poco en la actividad 07 porque anteriormente no habíamos creado un programa que funncionara tanto en p5js y con el microbit pero revisando unidades pasadas vi que ya nos habían dado elementos para abordarlo, era solo cuestión de recordarlo.


**Empezar a hacer: ¿Qué te habría ayudado a entender mejor?**

Las clases exlicativas a medida que avanzabamos en la unidad fueron muy útilesx y también me gustó que hubiese espacio para preguntas.


**Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa a diseñar y programar uno complejo? ¿Por qué?**
3, me pareció que tenía una dificultad adecuada y se podían llevar a cabo las actividades.

**Comentario adicional: ¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?**
No.




