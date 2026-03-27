<h1 align="center">Trabajo Práctico 1</h1>

## Comentario: los únicos ejercicios que revisten cierta dificultad son el 5 y el 6. No dejar de hacerlos (obtendrán un bonus que se contemplará para la calificación final de la materia).

## 1. Responder breve y claramente los siguientes incisos:

### a. Dados $\Sigma = \lbrace a, b, c \rbrace$ y $L = \lbrace a^n b^n c^n \mid n \geq  0 \rbrace$, obtener $\Sigma^* \cap L$, $\Sigma^* \cup L$ y $L^C$ (es decir, el complemento de $L$ con respecto a $\Sigma^*$).

1. Por regla general, si se cumple que $A \subseteq B$, entonces también se cumple que $A \cap B = A$. En este caso, como se sabe que todo lenguaje es un subconjunto de $\Sigma^*$, entonces se cumple que $L \subseteq \Sigma^*$. Por lo tanto, **se cumple que $\Sigma^* \cap L = L$**.
2. Otra regla general dice que si se cumple que $A \subseteq B$, entonces también se cumple que $A \cup B = B$. En este caso, dado que $L \subseteq \Sigma^*$, **se cumple que $\Sigma^* \cup L = \Sigma^*$**.
3. El complemento de un conjunto $A$ con respecto a un conjunto universal $U$ (en este caso, $\Sigma^*$) se define como el conjunto de todos los elementos de $U$ que NO están en $A$. Por lo tanto, **se cumple que $L^C = \Sigma^* - L$**.

### b. Definir el problema de la satisfactibilidad de las fórmulas booleanas en la forma de problema de búsqueda (visión de MT calculadora), de decisión (visión de MT reconocedora), y de enumeración (visión de MT generadora).

En los primeros 2 casos, la cadena de entrada $w$ es una fórmula booleana. En el tercer caso, la MT generadora no tiene cadena de entrada, es decir, la cinta inicia vacía.

En los 3 casos el alfabeto de la MT es $\Sigma = \lbrace 0, 1, \lnot, \land, \lor, (, ) \rbrace$, donde 0 simboliza falso, 1 simboliza verdadero, y los demás símbolos son los conectivos lógicos y los paréntesis.

Una cadena posible podría ser, por ejemplo, $w = (0 \land 1) \lor \lnot 0$. En este caso, el resultado es verdadero, ya que la fórmula se evalúa como $0 \land 1 = 0$, $\lnot 0 = 1$, y $0 \lor 1 = 1$.

1. **Problema de búsqueda**: La MT calculadora encuentra la primer asignación de valores de verdad a las variables que hace que la fórmula booleana $w$ sea verdadera. Es decir, la MT (1) deja en la cinta la asignación de valores de verdad a las variables que hace que la fórmula sea verdadera, o (2) borra toda la cinta si tal asignación no existe.
2. **Problema de decisión**: La MT reconocedora decide si la fórmula booleana $w$ es satisfactible o no. Es decir, la MT para en $q_A$ si existe alguna asignación de valores de verdad a las variables que hace que la fórmula sea verdadera, y para en $q_R$ si tal asignación no existe.
3. **Problema de enumeración**: La MT generadora genera una por una todas las fórmulas booleanas satisfactibles, que son infinitas.

### c. ¿Qué postula la Tesis de Church-Turing?

La tesis de Church-Turing postula que todo algoritmo, es decir, todo proceso mecánico de resolución de problemas, puede ser simulado por una máquina de Turing. En otras palabras, cualquier función que pueda ser computada por un algoritmo puede ser computada por una máquina de Turing. Si bien esta tesis no es un teorema demostrable, está ampliamente aceptada en la comunidad científica y matemática y es fundamental para la teoría de la computación.

### d. ¿Cuándo dos MT son equivalentes? ¿Cuándo dos modelos de MT son equivalentes?

Dos MT son equivalentes si reconocen el mismo lenguaje, es decir, si resuelven el mismo problema de decisión. Formalmente, dos MT $M_1$ y $M_2$ son equivalentes si $L(M_1) = L(M_2)$, donde $L(M)$ es el lenguaje que reconoce la MT $M$.

Dos modelos de MT son equivalentes si pueden simularse de forma mutua, es decir, si dada una MT del modelo A existe una MT equivalente en el modelo B, y viceversa. Por ejemplo, una MT con varias cintas puede simular a una MT con una sola cinta, y una MT con una sola cinta puede simular a una MT con varias cintas. Por lo tanto, ambos modelos son equivalentes.

### e. ¿En qué se diferencian los lenguajes recursivos, los lenguajes recursivamente enumerables no recursivos, y los lenguajes no recursivamente enumerables?

Los lenguajes **recursivos** son aquellos para los cuales existe al menos una MT que los reconoce y además siempre se detiene (es decir, jamás entra en loop). En otras palabras, para cada cadena de entrada, la MT se detiene en el estado $q_A$ si la cadena pertenece al lenguaje, y se detiene en el estado $q_R$ si la cadena no pertenece al lenguaje.

Los lenguajes **recursivamente enumerables no recursivos** son aquellos para los cuales existe al menos una MT que los reconoce, pero no existe ninguna MT que los reconozca y siempre se detenga. En otras palabras, para cada cadena de entrada, la MT se detiene en el estado $q_A$ si la cadena pertenece al lenguaje, pero si la cadena no pertenece al lenguaje, la MT puede o bien detenerse en el estado $q_R$ o bien entrar en loop.

Los lenguajes **no recursivamente enumerables** son aquellos para los cuales no existe ninguna MT que los reconozca. Es decir, no existe ninguna MT que siempre se detenga en el estado $q_A$ para cada cadena de entrada que pertenece al lenguaje. Incluso para este tipo de cadenas válidas, la MT puede loopear.

### f. Probar que $R \subseteq RE \subseteq \mathcal{L}$. Ayuda: usar las definiciones.

1. **$R \subseteq RE$**:
   1. $R$ es el conjunto de lenguajes para los cuales existe al menos una MT que los reconoce y siempre se detiene.
   2. $RE$ es el conjunto de lenguajes para los cuales existe al menos una MT que los reconoce, pero no siempre se detiene para las cadenas que no pertenecen al lenguaje.
   3. Para probar que $R \subseteq RE$, es necesario probar que para todo lenguaje $L$ que pertenece a $R$, $L$ también pertenece a $RE$.
   4. Sea $L \in R$. Entonces existe una MT $M$ que reconoce $L$ y siempre se detiene. Esto implica que para cada cadena de entrada, $M$ se detiene en el estado $q_A$ si la cadena pertenece a $L$, y se detiene en el estado $q_R$ si la cadena no pertenece a $L$.
   5. Dado que la definición de $RE$ no exige que la MT loopee para cadenas que no pertenecen al lenguaje, si no que también permite que la MT se detenga en el estado $q_R$, entonces $M$ también cumple con la definición de una MT que reconoce un lenguaje en $RE$. Por lo tanto, $L \in RE$.
   6. Se concluye que $R \subseteq RE$.
2. **$RE \subseteq \mathcal{L}$**:
   1. $RE$ es el conjunto de lenguajes para los cuales existe al menos una MT que los reconoce, pero no siempre se detiene para las cadenas que no pertenecen al lenguaje.
   2. $\mathcal{L}$ es el conjunto de todos los lenguajes posibles en el universo.
   3. La inclusión se cumple trivialmente, ya que obviamente todo lenguaje que pertenece a $RE$ también pertenece a $\mathcal{L}$, dado que $\mathcal{L}$ es el conjunto de todos los lenguajes posibles y $RE$ contiene lenguajes válidos. Por lo tanto, $RE \subseteq \mathcal{L}$.

Por transitividad de la inclusión, se concluye que $R \subseteq RE \subseteq \mathcal{L}$.

### g. Explicar por qué (a) el lenguaje $\Sigma^*$ de todas las cadenas, (b) el lenguaje vacío $\emptyset$, y (c) cualquier lenguaje finito, son recursivos. Alcanza con dar la idea general. Ayuda para (c): por cada cadena del lenguaje podría definirse un conjunto específico de transiciones.

1. El lenguaje $\Sigma^*$ es recursivo porque existe una MT que lo reconoce y siempre se detiene. La MT simplemente tiene, en su función de transición, que para TODO símbolo del alfabeto $\Sigma$, transiciona al estado de aceptación $q_A$. De esta manera, sea cual sea la cadena de entrada, la MT se detiene en el estado $q_A$.
2. El lenguaje vacío $\emptyset$ es recursivo porque existe una MT que lo reconoce y siempre se detiene. La MT simplemente tiene, en su función de transición, que para TODO símbolo del alfabeto $\Sigma$, transiciona al estado de rechazo $q_R$. De esta manera, sea cual sea la cadena de entrada, la MT se detiene en el estado $q_R$.
3. Cualquier lenguaje finito es recursivo porque existe una MT que lo reconoce y siempre se detiene. Como el lenguaje es finito, se pueden enumerar todas las cadenas que pertenecen al lenguaje. La MT puede simplemente comparar de forma iterativa la cadena $w$ que recibió con cada una de las cadenas del lenguaje. Si $w$ coincide con alguna de las cadenas del lenguaje, la MT transiciona al estado de aceptación $q_A$ y se detiene. Si $w$ no coincide con ninguna de las cadenas del lenguaje, la MT transiciona al estado de rechazo $q_R$ y se detiene. Como el lenguaje es finito, esta comparación se puede realizar en un número finito de pasos, garantizando que la MT siempre se detiene.

### h. Explicar por qué no es correcta la siguiente prueba de que si $L \in RE$, también $L^C \in RE$: dada una MT $M$ que acepta $L$, entonces la MT $M'$, igual que $M$ pero con los estados finales permutados, acepta $L^C$.

La prueba es incorrecta porque si bien se pueden invertir los estados finales $q_A$ y $q_R$, no hay forma de invertir los loopeos que la MT $M$ puede cometer para las cadenas que no pertenecen a $L$. Es decir, si $M$ loopea para una cadena $w \notin L$, entonces $M'$ también loopeará para esa misma cadena $w$, y por lo tanto no la aceptará cuando en realidad SI debería aceptarla, por definición de complemento de un lenguaje. Por lo tanto, $M'$ no reconoce $L^C$, y la prueba es incorrecta.

## 2. Explicar (dar la idea general) cómo una MT que en un paso no puede simultáneamente modificar un símbolo y moverse, puede simular (ejecutar) una MT que sí lo puede hacer.

Se tiene una MT $M$ que cuando modifica un símbolo, se queda quieta. Cuando no modifica un símbolo, se puede mover a la derecha o a la izquierda. Se puede usar a esta máquina $M$ para simular a una MT $M'$ que sí puede modificar un símbolo y moverse al mismo tiempo, de la siguiente manera:

- Si $M'$ tiene una transición que modifica un símbolo y se mueve a la derecha, entonces $M$ puede simular esta transición en dos pasos: primero, $M$ modifica el símbolo sin moverse, se dirige a un estado intermedio y luego, en el siguiente paso, $M$ se mueve a la derecha sin modificar el símbolo y pasa al estado destino original.
- Si $M'$ tiene una transición que modifica un símbolo y se mueve a la izquierda, entonces $M$ puede simular esta transición en dos pasos: primero, $M$ modifica el símbolo sin moverse, se dirige a un estado intermedio y luego, en el siguiente paso, $M$ se mueve a la izquierda sin modificar el símbolo y pasa al estado destino original.

## 3. Describir la idea general de una MT con varias cintas que acepte, de la manera más eficiente posible (menor cantidad de pasos), el lenguaje $L = \lbrace a^n b^n c^n \mid n \geq 0 \rbrace$

$L = \lbrace \lambda, abc, aabbcc, aaabbbccc, ... \rbrace$

El objetivo de la MT a construir es verificar que (1) la cadena de entrada tiene la forma $a^n b^n c^n$, es decir, que primero aparecen $n$ símbolos $a$, luego $n$ símbolos $b$, y finalmente $n$ símbolos $c$, y (2) que el número de símbolos $a$, $b$ y $c$ es el mismo.

Se puede usar una MT con 4 cintas donde la primer cinta contiene la cadena de entrada, y las otras 3 cintas se usan como auxiliares para contar el número de símbolos $a$, $b$ y $c$:

1. La MT comienza en la cinta 1, lee la cadena de entrada símbolo por símbolo y hace lo siguiente, en **una única pasada por la cinta 1**:
   1. Recorre todos los símbolos $a$ que encuentra y por cada uno escribe una $X$ en la cinta 2.
   2. Luego, recorre todos los símbolos $b$ que encuentra y por cada uno escribe una $X$ en la cinta 3.
   3. Finalmente, recorre todos los símbolos $c$ que encuentra y por cada uno escribe una $X$ en la cinta 4.
   4. Si en cualquier momento en este recorrido la máquina encuentra que el formato de la cadena no es correcto (por ejemplo, encuentra un símbolo $c$ luego de haber recorrido todas las $a$), entonces la MT se detiene en el estado de rechazo $q_R$.
2. Luego la máquina recorre las cintas 2, 3 y 4 en paralelo desde el inicio de cada una, avanzando hacia la derecha si en las tres cintas se lee una $X$, aceptando si en las tres cintas hay blancos al mismo tiempo, y rechazando en cualquier otro caso, por ejemplo que la cinta 2 tenga una $X$ mientras que las otras dos tienen blanco.

## 4. Probar:

### a. La clase $R$ es cerrada con respecto a la operación de unión. Ayuda: la prueba es similar a la desarrollada para la intersección.

### b. La clase $RE$ es cerrada con respecto a la operación de intersección. Ayuda: la prueba es similar a la desarrollada para la clase $R$.

## 5. Sean $L_1$ y $L_2$ dos lenguajes recursivamente enumerables de números naturales codificados en unario (por ejemplo, el número 5 se representa con 11111). Probar que también es recursivamente enumerable el lenguaje $L = \lbrace x \mid \text{x es un número natural codificado en unario y existen y, z tales que y + z = x, con y} \in L_1, z \in L_2 \rbrace$. Ayuda: la prueba es similar a la vista en clase, de la clausura de la clase $RE$ con respecto a la operación de concatenación.

## 6. Dada una MT $M_1$ con alfabeto $\Gamma = \lbrace 0, 1, B \rbrace$:

### a. Construir una MT $M_2$, utilizando la MT $M_1$, que acepte, cualquiera sea su cadena de entrada, si y solo si la MT $M_1$ acepta al menos una cadena. Ayuda: Si $M_1$ acepta al menos una cadena, entonces existe al menos una cadena de símbolos $0$ y $1$, de tamaño $n$, tal que $M_1$ la acepta en $k$ pasos. Teniendo en cuenta esto, pensar cómo $M_2$ podría simular $M_1$ considerando todas las cadenas de símbolos $0$ y $1$ hasta encontrar eventualmente una que la acepte $M_1$ (¡cuidándose de los casos en que $M_1$ entre en loop!).

### b. ¿Se puede construir además una MT $M_3$, utilizando la MT $M_1$, que acepte, cualquiera sea su cadena de entrada, si y solo si la MT $M_1$ acepta a lo sumo una cadena? Justificar.
