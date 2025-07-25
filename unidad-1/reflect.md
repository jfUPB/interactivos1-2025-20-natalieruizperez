# Unidad 1

## 🤔 Fase: Reflect

### Actividad 07 -Autoevaluación
---
#### Parte 1: recuperación de conocimiento (Retrieval Practice)

**1. Basándote en los ejemplos que vimos de sistemas físicos interactivos al iniciar el curso, describe las tres características que definen a un sistema físico interactivo.**

  Un sistema físico interactivo se caracteriza por ser automatizado, recibir un input y dar como respuesta un output.

**2. Explica el modelo input-process-output de Patrick Hübner usando como ejemplo el sistema que construiste con micro:bit y p5.js en la Actividad 06. ¿Cuál fue el input, cuál fue el proceso y cuál fue el output?**

  En este sistema los inputs serían los botones y el cable que permite conectar el microbit al pc (serial). Los outputs serían lo que se ve en la patalla del computador como el círculo rosado, cuando se actualiza la posición de este mismo y también el botón que aparece en la pantalla para conectar o desconectar el microbit.

**3. ¿Cuál es la función de la línea uart.write('A') en el código del micro:bit y qué función en p5.js se encarga de “escuchar” ese mensaje?**

  La función de la línea uart.write('A') permite devolver un mensaje, es decir al presionar el botón A se hará una comunicación entre el microbit y el pc. La función que se encarga de escuchar el mensaje creo que sería la que permite leer si está disponible el puerto.

**4. ¿Cuál es la diferencia fundamental entre el arte/diseño tradicional y el arte/diseño generativo?**

  La diferencia fundamental entre el arte/diseño tradicional y el arte/diseño generativo consiste en que el generativo sigue unas reglas específicas estipuladas por el programador, estás reglas pueden ser modificadas en parámetros específicos para obtener un resultado más natural y humano, dándole aleatoriedad. Por otro lado, el arte o diseño tradicional consiste en hacer piezas a mano que no son posibles automatizar.

**5. Imagina que quieres que un círculo en p5.js cambie a un color aleatorio cada vez que sacudes el micro:bit. Describe qué tendrías que programar en el micro:bit y qué tendrías que programar en p5.js para lograrlo.**

  Todavía no he interiorizado bien cómo programar de la nada, considero que sería capaz de hacerlo tomando uno de los ejemplos de la unidad y modificándolo. En el microbit tendría que poner una línea que permita acceder al acelerómetro para saber cuándo está siendo sacudido y en el p5.js pondría que si está siendo sacudido se rellene con un color aleatorio.

---
#### Parte 2: reflexión sobre tu proceso (Metacognición)

**1. ¿Qué fue más desafiante para ti en esta unidad: la parte conceptual (entender qué es un sistema físico interactivo) o la parte técnica (hacer que el micro:bit y p5.js se comunicaran)? ¿Por qué?**

  Lo más desafiante para mí en esta unidad fue entender qué tipo de código debía de ir en el microbit y cuál en el p5.js, normalmente hubiese optado por poner todo el código en una sola plataforma por temas de comodidad pero entendí que al manejar este sistema era necesario usar ambos para obtener los resultados deseados.

**2. Describe el momento “¡Aha!” que tuviste cuando lograste que una acción en el micro:bit (presionar un botón, sacudirlo) tuviera un efecto visible en el canvas de p5.js por primera vez. ¿Qué fue lo que entendiste en ese instante?**

  La primera vez que usé un microbit me emocióno ver cómo al presionar el botón "send love" era posible cambiar la imagen que aparecía en el microbit. Tenía conocimientos previos y ya sabía que al presionar el botón podía hacer que lo que se veía en la pantalla se modificara, pero no tenía idea de que algo en la pantalla podía modificar el microbit. Fue un descubrimiento totalmente nuevo.

**3. Al inicio de la unidad te pregunté: “¿Este curso para qué me sirve?”. Después de experimentar y construir tu primer prototipo, ¿Cómo ha cambiado o se ha vuelto más concreta tu respuesta a esa pregunta?**

  Este curso sirve para crear sistemas interactivos con los cuales los usarios pueden interactuar mediante inputs y el sistema producirá un output. La verdad mi opinión acerca de para qué sirve el curso no ha cambiado significativamente, lo que si cambio fue mi comprensión de cómo funcionan estos sistemas y de los procesos necesarios para crearlos. Usualmente al ver en un concierto un fondo generativo no se suele reflexionar acerca de qué se tuvo que hacer para obtener ese resultado pero con estos conocimientos ya es posible hacerse una idea de todo el trabajo que está detrás.

**4. El tutorial de la Actividad 05 te llevó paso a paso. ¿Cómo te sentiste con ese método de aprendizaje? ¿Te dio seguridad o preferirías haberlo intentado por tu cuenta desde el principio?**

  Fue mi método favorito, me gustó revisar al mismo tiempo el código con el profesor ya que me permitió tomar nota y hacer preguntas en el momento que me serivirían más adelante para responder la actividad 06. Si lo hubiese hecho desde el principio completamente sola me hubiese sentido muy perdida y probablemente me hubiese costado entender.

---
### Actividad 08 - Coevaluación

**1. Encuentra un compañero de trabajo.**

  Fabricio Toro

**2. Intercambien las URLs de sus bitácoras de aprendizaje.**

  https://github.com/jfUPB/interactivos1-2025-20-CrockerHacker101/blob/unidad1/apply/unidad-1/apply.md

**3. Concéntrate en la Actividad 06: control de movimiento con micro:bit de tu compañero. Lee su código (Python y JavaScript). Tu compañero resolvió el problema de manera diferente a ti, qué hizo diferente, qué aprendiste de su solución. En tu bitácora documenta lo anterior y escribe, como si le estuvieras explicando, lo que tú hiciste y por qué es diferente a lo que hizo tu compañero.**

  Al observar la solución de mi compañero me gustó en especial una línea de código que no conocía que permitía suavizar el movimiento del círculo y hacer que se viera más fluido, me hubiese gustado implementar una solución así en mi código ya que mi círculo se movía de forma muy robótica.

---
### Actividad 09 - Feedback

**1. Continuar: ¿Qué actividad, video o ejemplo de esta unidad te resultó más inspirador o te ayudó más a entender el potencial de los sistemas físicos interactivos?**

  La actividad 05 fue la que me ayudó más a entender el proceso y cómo se podía crear un sistema interactivo ya que en esta supe entender el código y entender qué pasaba línea por línea.

**2. Dejar de hacer: ¿Hubo alguna parte que te pareció demasiado abstracta, muy rápida o confusa? ¿Hay algo que crees que podríamos cambiar para que sea más claro?**

  La verdad me siento satisfecha en general con el curso, me pareció que tenía un buen ritmo. No cambiaría nada.

**3. Empezar a hacer: ¿Qué te genera más curiosidad ahora? ¿Te gustaría explorar más sensores del micro:bit (luz, temperatura), crear visualizaciones más complejas en p5.js o ver más ejemplos de proyectos artísticos?**

  Me encantaría crear visualizaciones más complejas en p5.js o hacer algo más artístico como crear visuales generativas que podrían ir en conciertos.

**4. Balance inspiración vs. técnica: ¿Cómo sentiste el equilibrio entre ver los videos inspiradores de la Actividad 01 y la parte técnica de conectar las herramientas en las actividades 03-06?**

  Sentí buen equilibrio entre las actividades, la dificultad no subía de repente si no que era de poco a poco.

**5. Comentario adicional: ¿Hay algo más que quieras compartir sobre tu experiencia en esta unidad introductoria?**

  Me gustó la primera unidad, considero que me ha dado herramientas para entender mejor en qué consisten los sistemas interactivos y uno de los procesos.

