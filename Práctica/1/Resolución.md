<h1 align="center">Trabajo Práctico 1</h1>

## Comentario: los únicos ejercicios que revisten cierta dificultad son el 5 y el 6. No dejar de hacerlos (obtendrán un bonus que se contemplará para la calificación final de la materia).

## 1. Responder breve y claramente los siguientes incisos:

### a. Dados $\Sigma = \lbrace a, b, c \rbrace$ y $L = \lbrace a^n b^n c^n \mid n \geq  0 \rbrace$, obtener $\Sigma^* \cap L$, $\Sigma^* \cup L$ y $L^C$ (es decir, el complemento de $L$ con respecto a $\Sigma^*$).

### b. Definir el problema de la satisfactibilidad de las fórmulas booleanas en la forma de problema de búsqueda (visión de MT calculadora), de decisión (visión de MT reconocedora), y de enumeración (visión de MT generadora).

### c. ¿Qué postula la Tesis de Church-Turing?

### d. ¿Cuándo dos MT son equivalentes? ¿Cuándo dos modelos de MT son equivalentes?

### e. ¿En qué se diferencian los lenguajes recursivos, los lenguajes recursivamente enumerables no recursivos, y los lenguajes no recursivamente enumerables?

### f. Probar que $R \subseteq RE \subseteq \mathcal{L}$. Ayuda: usar las definiciones.

### g. Explicar por qué (a) el lenguaje $\Sigma^*$ de todas las cadenas, (b) el lenguaje vacío $\emptyset$, y (c) cualquier lenguaje finito, son recursivos. Alcanza con dar la idea general. Ayuda para (c): por cada cadena del lenguaje podría definirse un conjunto específico de transiciones.

### h. Explicar por qué no es correcta la siguiente prueba de que si $L \in RE$, también $L^C \in RE$: dada una MT $M$ que acepta $L$, entonces la MT $M'$, igual que $M$ pero con los estados finales permutados, acepta $L^C$.

## 2. Explicar (dar la idea general) cómo una MT que en un paso no puede simultáneamente modificar un símbolo y moverse, puede simular (ejecutar) una MT que sí lo puede hacer.

## 3. Describir la idea general de una MT con varias cintas que acepte, de la manera más eficiente posible (menor cantidad de pasos), el lenguaje $L = \lbrace a^n b^n c^n \mid n \geq 0 \rbrace$

## 4. Probar:

### a. La clase $R$ es cerrada con respecto a la operación de unión. Ayuda: la prueba es similar a la desarrollada para la intersección.

### b. La clase $RE$ es cerrada con respecto a la operación de intersección. Ayuda: la prueba es similar a la desarrollada para la clase $R$.

## 5. Sean $L_1$ y $L_2$ dos lenguajes recursivamente enumerables de números naturales codificados en unario (por ejemplo, el número 5 se representa con 11111). Probar que también es recursivamente enumerable el lenguaje $L = \lbrace x \mid \text{x es un número natural codificado en unario y existen y, z tales que y + z = x, con y} \in L_1, z \in L_2 \rbrace$. Ayuda: la prueba es similar a la vista en clase, de la clausura de la clase $RE$ con respecto a la operación de concatenación.

## 6. Dada una MT $M_1$ con alfabeto $\Gamma = \lbrace 0, 1, B \rbrace$:

### a. Construir una MT $M_2$, utilizando la MT $M_1$, que acepte, cualquiera sea su cadena de entrada, si y solo si la MT $M_1$ acepta al menos una cadena. Ayuda: Si $M_1$ acepta al menos una cadena, entonces existe al menos una cadena de símbolos $0$ y $1$, de tamaño $n$, tal que $M_1$ la acepta en $k$ pasos. Teniendo en cuenta esto, pensar cómo $M_2$ podría simular $M_1$ considerando todas las cadenas de símbolos $0$ y $1$ hasta encontrar eventualmente una que la acepte $M_1$ (¡cuidándose de los casos en que $M_1$ entre en loop!).

### b. ¿Se puede construir además una MT $M_3$, utilizando la MT $M_1$, que acepte, cualquiera sea su cadena de entrada, si y solo si la MT $M_1$ acepta a lo sumo una cadena? Justificar.
