# Unidad 2


## 🤔 Fase: Reflect

### Actividad 06

#### Parte 1: recuperación de conocimiento (Retrieval Practice)

**Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?**
Una maquina de estados es aquella que permite crear una secuencia de sucesos. A través de una máquina de estados es posible cambiar lo que sucede en el programa. Usualmente el primer estado es llamado init que es el inicial y luego cambia a otro estado, el programa nunca vuelve a init ya que este sirve para preparar lo que va a suceder y dar valores iniciales.

**Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender un temporizador y botones “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit. ¿Qué problema soluciona en comparación con usar funciones como sleep()?**
La máquina de estados es más útil porque gracias a esta es posible hacer cosas y al mismo tiempo hace que el programa

**Imagina que tienes que añadir una nueva funcionalidad a la bomba temporizada: si se agita (shake) el micro:bit mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?**

**Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.**

#### Parte 2: reflexión sobre tu proceso (Metacognición)

**1. ¿Qué parte del diseño de la bomba temporizada te resultó más desafiante: crear el diagrama de estados (Actividad 04) o traducir ese diagrama a código MicroPython (Actividad 05)? ¿Por qué?**
El diagrama me pareció más desafiante ya que no habíamos visto antes un cuadro que tuviese una flecha que va a si mismo, además que había que pensar en la lógica del programa. Para la parte de creación del código como ya había pensado en cómo sería el diagrama solo fue organizar las palabras para que tuviesen sentido con python y buscar cómo interactuar con el touch y mostrar el texto de la bomba.

**2. Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?**
Un error que tuve 

**3. El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?**

Para el diagrama lo empecé en clase para aprovechar el tiempo al máximo y poder preguntarle al profeesor si lo que hacía era correcto, si no hubiese hecho eso y lo hubiese abordado todo por mi cuenta lo más posible es que tuviese errores en ya que antes no había hecho un diagrama para un microbit y por consiguiente errores en el código. Para el código lo primero que hice fue establecer los valores iniciales y después declarar los estados. Después de eso me fui estado por estado poniendo los eventos y acciones. 

**4. Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?**
Estas máquinas de estados pueden ser muy útiles a la hora de programar en unity. Lo que más me gusta de este curso es que la lógica nos sirve no solamente para el curso si no también para aplicarlo en códigos futuros.

  



