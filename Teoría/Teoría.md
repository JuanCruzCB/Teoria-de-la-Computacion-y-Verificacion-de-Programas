<h1 align="center">Clase 1 - 10 de marzo, 2026</h1>

## Introducción (historia)

- **Inicios del siglo XX**: Se empieza a buscar un esquema mecánico para demostrar todas las verdades matemáticas (Hilbert).
- **1931**: Gödel demuestra que hay verdades matemáticas que no pueden ser demostradas mecánicamente.
- **1936**: Church y Turing demuestran que hay enunciados matemáticos que no se puede decidir mecánicamente si son verdaderos o falsos (problema de la parada). Origen de la computación. Máquina de Turing como modelo de computación.
- **Década de los 40**: Primeras computadoras.
- **Década de los 60**: Origen de la complejidad computacional, problemas fáciles y difíciles en términos de tiempo y espacio. Algoritmos probabilísticos y cuánticos, pruebas interactivas, inteligencia artificial, etc.
- **Década de los 70**: Origen de la correctitud de programas (verificación formal, semántica de lenguajes). Evoluciona a la verificación semi-automática (con asistencia) y la verificación automática (model checking), etc.

## Repaso de conceptos básicos de matemática

### Conjunto

- Un conjunto es una colección de elementos.
- $A = \lbrace a, b, c \rbrace$ es un conjunto con tres elementos: $a$, $b$ y $c$. Se dice que $a$, $b$ y $c$ pertenecen (o son miembros de) $A$, lo que se denota como $a \in A$, $b \in A$ y $c \in A$.

### Igualdad de conjuntos

- Dos conjuntos $A$ y $B$ son iguales, denotado como $A = B$, si tienen los mismos elementos.
- $A = \lbrace casa, árbol, cielo \rbrace$ y $B = \lbrace árbol, cielo, casa \rbrace$ son iguales porque contienen los mismos elementos, aunque estén en diferente orden.

### Subconjunto

- Un conjunto $A$ es un subconjunto de otro conjunto $B$, denotado como $A \subseteq B$, si todos los elementos de $A$ también son elementos de $B$. La inclusión puede ser estricta, denotada como $A \subset B$, si $A$ es un subconjunto de $B$ pero los conjuntos NO son iguales. Si no es estricta, denotada como $A \subseteq B$, entonces $A$ puede ser igual a $B$.
- $\lbrace 1, 2 \rbrace \subseteq \lbrace 1, 2, 3, 5 \rbrace$ y también se cumple que $\lbrace 1, 2 \rbrace \subset \lbrace 1, 2, 3, 5 \rbrace$.

### Intersección

- Dados dos conjuntos $A$ y $B$, la intersección de $A$ y $B$, denotada como $A \cap B$, es el conjunto de elementos que están en $A$ **y** en $B$.
- $\lbrace 1, 2, 3, 4, 5 \rbrace \cap \lbrace 4, 5, 6 \rbrace = \lbrace 4, 5 \rbrace$

### Unión

- Dados dos conjuntos $A$ y $B$, la unión de $A$ y $B$, denotada como $A \cup B$, es el conjunto de elementos que están en $A$ **o** en $B$ (o en ambos).
- $\lbrace 1, 2, 3, 4, 5 \rbrace \cup \lbrace 4, 5, 6 \rbrace = \lbrace 1, 2, 3, 4, 5, 6 \rbrace$

### Diferencia

- Dados dos conjuntos $A$ y $B$, la diferencia de $A$ y $B$, denotada como $A - B$, es el conjunto de elementos que están en $A$ y no están en $B$.
- $\lbrace 1, 2, 3, 4, 5 \rbrace - \lbrace 4, 5, 6 \rbrace = \lbrace 1, 2, 3 \rbrace$

### Funciones

- Una función de un conjunto $A$ a un conjunto $B$, denotada como $f: A \rightarrow B$, es un conjunto de pares ordenados $(a, b)$ donde $a \in A$ y $b \in B$, tales que a lo sumo existe un par $(a, b)$ para cada $a \in A$. Es decir, cada elemento de $A$ se asigna a lo sumo a un elemento de $B$.
- $f(a) = b$ expresa que el par ordenado $(a, b)$ pertenece a la función $f$.
- Por ejemplo:
  - $A = \lbrace 1, 2, 3, 4 \rbrace$
  - $B = \lbrace m, n, o \rbrace$
  - $\lbrace (1, m), (2, n), (3, n) \rbrace$ es una función $f$ de $A$ a $B$.
  - También se puede definir así:
    - $f(1) = m$
    - $f(2) = n$
    - $f(3) = n$.
  - El conjunto $A$ es el **dominio** y el conjunto $B$ es el **codominio** de la función $f$.
- $f$ es **inyectiva** si cada elemento de $B$ es asignado como mucho a un elemento de $A$. Es decir, no hay dos elementos distintos de $A$ que se asignen al mismo elemento de $B$.
- $f$ es **suryectiva** si cada elemento de $B$ es asignado a al menos un elemento de $A$. Es decir, todos los elementos de $B$ son alcanzados por la función $f$.
- $f$ es **biyectiva** si es inyectiva y suryectiva a la vez.
- En el ejemplo, la función $f$ no es inyectiva porque el elemento $n$ de $B$ es asignado a dos elementos distintos de $A$ (2 y 3), y tampoco es suryectiva porque el elemento $o$ de $B$ no es asignado a ningún elemento de $A$.

### Alfabeto

- Un alfabeto es un conjunto finito de símbolos. Se denota comúnmente como $\Sigma$.
- $\Sigma = \lbrace a, b, c \rbrace$ es un alfabeto de 3 símbolos.

### Lenguaje

- Un lenguaje sobre un alfabeto $\Sigma$ es un conjunto de cadenas finitas formadas con los símbolos de $\Sigma$.
- Si $\Sigma = \lbrace a, b, c \rbrace$, un lenguaje $L$ con alfabeto $\Sigma$ podría ser $L = \lbrace aaa, b, ababab, ccb \rbrace$.
- Las operaciones típicas entre lenguajes son las mismas que para los conjuntos: intersección, unión y diferencia. Además se agregan:
  - El complemento respecto a otro lenguaje que lo incluye.
  - El complemento respecto a todas las cadenas posibles sobre el alfabeto (denotado como $\Sigma^*$).
  - La concatenación de dos lenguajes $L_1$ y $L_2$, denotada como $L_1 \cdot L_2$, que es el lenguaje formado por todas las cadenas que se pueden obtener concatenando una cadena de $L_1$ con una cadena de $L_2$.

### Grafo

- Un grafo es un par $G = (V, E)$ donde $V$ es un conjunto de **vértices** y $E$ es un conjunto de **arcos**.

![](https://i.imgur.com/Izk1gGZ.png)

- En este grafo tenemos 10 vértices y 11 arcos.
- Los vértices 1 y 2 son **adyacentes**, es decir, están conectados por un arco.
- Los arcos (1, 2) y (2, 3) son **adyacentes**, es decir, comparten un vértice.
- La secuencia de vértices (1, 2, 3, 6, 7, 9, 10) representa un **camino** del vértice 1 al vértice 10.

### Fórmula booleana

- Una fórmula booleana es una fórmula lógica que se obtiene combinando variables booleanas de valor de verdad Verdadero (V) o Falso (F), usando los operadores lógicos AND ($\land$), OR ($\lor$) y NOT ($\lnot$).
- Por ejemplo $\varphi = (x_1 \lor x_2) \land (\lnot x_1 \lor \lnot x_2)$ es una fórmula booleana con variables booleanas $x_1$ y $x_2$.
- La semántica de los operadores lógicos es la siguiente:
  - $\varphi = x_1 \land x_2$ es V si y solo si $x_1$ es V y $x_2$ es V.
  - $\varphi = x_1 \lor x_2$ es V si y solo si $x_1$ es V o $x_2$ es V (o ambos).
  - $\varphi = \lnot x$ es V si y solo si $x$ es F.
- Por ejemplo, dada la fórmula booleana $\varphi = (x_1 \lor x_2) \land (\lnot x_1 \lor \lnot x_2)$, si $x_1 = V$ y $x_2 = F$, entonces $\varphi$ es V, pero si $x_1 = V$ y $x_2 = V$, entonces $\varphi$ es F.
- Una fórmula booleana $\varphi$ es satisfacible si existe al menos una asignación de valores de verdad que la hace verdadera.
  - Por ejemplo, la fórmula anterior es satisfactible porque existe una asignación de valores de verdad (por ejemplo, $x_1 = V$ y $x_2 = F$) que la hace verdadera.
  - En cambio, la fórmula $\varphi = x_1 \land \lnot x_1$ no es satisfactible porque no existe ninguna asignación de valores de verdad que la haga verdadera.

## Máquina de Turing

### Concepto

- Modelización muy simple de una computadora.
- Está aceptada universalmente para estudiar la computabilidad y la complejidad computacional de los problemas.

### Cinta

- La máquina de Turing tiene una cinta infinita dividida en celdas.
- Cada celda almacena un único símbolo del alfabeto de la máquina, denotado como $\Gamma$.
- La unidad de control, también llamada cabezal, siempre se encuentra en un estado determinado de un conjunto finito de estados denotado como $Q$.
- Al iniciar la computación, la entrada se delimita por símbolos blancos $B$ a ambos lados, y el cabezal apunta al primer símbolo de la entrada.

### Definición formal

- Una Máquina de Turing es una tupla $M = (Q, \Gamma, \delta, q_0, q_A, q_R)$ donde:
  - $Q$ es el conjunto finito de **estados** de $M$.
  - $\Gamma$ es el **alfabeto** de $M$, el cual incluye al símbolo blanco $B$. Las cadenas de entrada no pueden contener el símbolo blanco.
  - $\delta$ es la **función de transición** de $M$ que especifica su comportamiento. Dado un estado corriente de $Q$ y un símbolo corriente de $\Gamma$, la máquina:
    - Pasa eventualmente a un nuevo estado de $Q$.
    - Modifica eventualmente el símbolo corriente de $\Gamma$.
    - Se mueve un lugar a la izquierda, a la derecha o se queda en el mismo lugar.
  - $q_0$ es el estado **inicial** de $M$.
  - $q_A$ es el estado de **aceptación** de $M$, en el cual la máquina para.
  - $q_R$ es el estado de **rechazo** de $M$, en el cual la máquina para.

### Problemas de decisión vs de búsqueda

- Un problema de búsqueda es un problema que requiere encontrar una solución específica. No son muy interesantes en cuanto a las máquinas de Turing.
- Un problema de decisión es un problema que tiene una respuesta de sí o no. Por ejemplo, dado un número entero $n$, determinar si $n$ es par o no. Estos problemas son los que se suelen estudiar con máquinas de Turing.
  - Dada una cadena de entrada, un "sí" equivale a que la máquina de Turing acepte la cadena, es decir, que eventualmente llegue al estado de aceptación $q_A$.
  - Dada una cadena de entrada, un "no" equivale a que la máquina de Turing rechace la cadena, es decir, que eventualmente llegue al estado de rechazo $q_R$.
- Dado lo anterior, una MT acepta o reconoce un lenguaje: el lenguaje formado por las cadenas que la máquina acepta. Por ejemplo, si una MT acepta todas las cadenas que representan números enteros pares, entonces el lenguaje que reconoce es el lenguaje de los números enteros pares. Se denota con $L(M)$ al lenguaje reconocido por la máquina de Turing $M$.
- Las palabras **problema** y **lenguaje** se usan indistintamente.

### Problemas computables decidibles

- Se trata de problemas de decisión donde dada una cadena de entrada $w$, la máquina de Turing $M$ **siempre se detiene** (es decir, llega eventualmente a un estado de aceptación o de rechazo) y responde correctamente si $w$ pertenece o no al lenguaje que reconoce $M$.
- Ejemplo: el problema de decidir si un número entero es par o no es un problema computable decidible, porque existe una máquina de Turing que siempre se detiene y responde correctamente si la cadena de entrada representa un número entero par o no.

### Problemas computables no decidibles

- Se trata de problemas de decisión donde dada una cadena de entrada $w$, la máquina de Turing $M$ **no siempre se detiene**, porque si bien siempre llega al estado de aceptación para las cadenas que sí pertenecen al lenguaje de la máquina, esto no se cumple para las cadenas que no pertenecen al lenguaje, porque la misma puede **loopear** indefinidamente.
- Ejemplo: el problema de la parada es un problema computable no decidible, porque existe una máquina de Turing que acepta todas las cadenas que representan programas que se detienen, pero no existe una máquina de Turing que rechace todas las cadenas que representan programas que no se detienen, porque la misma puede loopear indefinidamente.

### Problemas no computables

- Se trata de problemas de decisión que no poseen ninguna MT que los resuelva, es decir, ni siquiera hay garantía de que las cadenas que sí pertenecen al lenguaje de la máquina sean aceptadas, porque la máquina puede loopear indefinidamente tanto para las cadenas válidas como para las inválidas.
- Ejemplo: el problema de decidir si dos programas son equivalentes o no.

### Subdivisión de los problemas computables decidibles

- La principal clasificación de los problemas computables decidibles se hace en base a su **complejidad**:
  - **Tratables**: problemas que pueden ser resueltos por una máquina de Turing en tiempo polinomial respecto al tamaño de la cadena de entrada.
  - **Intratables**: problemas que no pueden ser resueltos por una máquina de Turing en tiempo polinomial respecto al tamaño de la cadena de entrada, sino que requieren un tiempo exponencial o incluso peor.

### Varias cintas

- Se trata de una variante de la máquina de Turing que tiene más de una cinta, cada una con su propio cabezal.
- La primer cinta de todas es la que contiene a la cadena de entrada. Las demás empiezan completamente vacías.
- La MT puede, en un solo paso, modificar el estado corriente, los símbolos corrientes de todas las cintas, y moverse distinto (o no) en cada cinta.
- Teorema: para toda MT de varias cintas, existe una MT de una sola cinta que reconoce el mismo lenguaje. Es decir, las MT de varias cintas no poseen más potencia computacional que las MT de una sola cinta, aunque sí pueden ser más eficientes en términos de tiempo de ejecución.

### Modelos equivalentes de MT

- Dos MT son equivalentes si aceptan el mismo lenguaje, es decir, si resuelven el mismo problema.
- Dos modelos de MT son equivalentes si dada una MT de un modelo existe una MT equivalente en el otro modelo.
- Ejemplos de modelos de MT equivalentes al modelo de MT clásico de una sola cinta:
  - MT de varias cintas.
  - MT con cintas semi-infinitas (solo infinitas a derecha o a izquierda).
  - MT con dos cintas y un único estado.
- Ejemplos de modelos computacionales equivalentes al modelo de las MT:
  - Máquinas RAM (acceso directo).
  - Circuitos booleanos.
  - Cálculo lambda.
  - Funciones recursivas.
  - Gramáticas.
  - Programas C.
- Lo anterior refuerza la tesis de Church-Turing.

### Lenguaje $\Sigma^*$

- Dado un alfabeto $\Sigma$, el lenguaje $\Sigma^*$ es el lenguaje formado por todas las cadenas finitas posibles que se pueden formar con los símbolos de $\Sigma$.
- Su primer elemento siempre es la cadena vacía $\lambda$, que no contiene ningún símbolo.
- Es un conjunto infinito contable.
- Cada uno de sus elementos es una cadena **finita**, por más larga que sea.
- Todo lenguaje $L$ es un subconjunto de $\Sigma^*$, es decir, $L \subseteq \Sigma^*$.

### MT calculadora

- Problema:
  - Construir una MT que reste dos números codificados en unario (es decir, el número $n$ se codifica como una cadena de $n$ símbolos iguales, por ejemplo, el número 3 se codifica como "111") y separados por un cero.
  - Por ejemplo, dada la entrada $11111101111$ hay que obtener la salida $11$ porque $6 - 4 = 2$.
- Solución: tachar el primer 1 **antes** del 0, luego el primer 1 **después** del 0, luego el segundo 1 antes del 0, luego el segundo 1 después del 0, y así sucesivamente hasta tachar al final el único 0 de la cadena.

### MT generadora

- Se trata de una MT que genera en una cinta de salida todas las cadenas del lenguaje que acepta.
- Por ejemplo, dado el lenguaje $L = \lbrace a^n b^n \mid n \geq 1 \rbrace$, la salida debe generar las cadenas $ab$, $aabb$, $aaabbb$, $aaaabbbb$, etc.
- Solución
  1. $i := 1$
  2. Imprimir $i$ veces $a$, imprimir $i$ veces $b$, e imprimir una coma
  3. $i := i + 1$ y volver al paso 2.
- **Teorema**: existe una MT que acepta un lenguaje $L$ si y solo si existe otra MT que genera el mismo lenguaje $L$. Es decir, si no es posible construir una MT que genere un lenguaje $L$, entonces tampoco es posible construir una MT que acepte el mismo lenguaje $L$, y viceversa.

### MT no determinística

- Se trata de una MT que para un mismo par (estado, símbolo) puede responder de más de una manera a la vez.
- Una MTN $M$ acepta una cadena de entrada $w$ si y solo si al menos una **computación** de $M$ acepta a $w$.
- Para simular una MTN con una MTD hay que recorrer en el peor caso todas sus computaciones. Asumiendo que toda computación hace a lo sumo $h$ pasos, entonces ejecutar secuencialmente todas las computaciones requiere unos $c^h$ pasos, siendo $c$ el grado del no determinismo (retardo exponencial).
- Las MTN no modelizan una computadora real, ya que haría falta un número infinito de procesadores. No son físicamente realizables, pero sirven para simplificar las descripciones de las MTD.

---

<h1 align="center">Clase 2 - 17 de marzo, 2026</h1>

## ?

---
