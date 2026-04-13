<h1 align="center">Trabajo Práctico 3</h1>

## 1. Responder breve y claramente:

### a. Probar que $n^3 = O(2^n)$.

### b. Probar que si $T_1(n) = O(T_2(n))$, entonces $TIME(T_1(n)) ⊆ TIME(T_2(n))$.

### c. ¿Qué formulan la Tesis de Church-Turing y la Tesis Fuerte de Church-Turing?

### d. ¿Por qué si un lenguaje pertenece a $P$ también su complemento pertenece a $P$?

### e. Sea $L$ un lenguaje de $NP$. Explicar por qué los certificados de $L$ miden un tamaño polinomial con respecto al tamaño de las cadenas de entrada.

### f. Probar que $NP \neq \text{CO-NP}$ implica $P \neq NP$.

### g. Mostrar un esquema de prueba de la transitividad de las reducciones polinomiales.

### h. Probar que si $L_1 \leq_P L_2$ y $L_2 \in P (NP)$, entonces $L_1 \in P (NP)$. En otras palabras, $L_2$ es tan o más difícil que $L_1$, en el marco de la complejidad temporal.

### i. ¿Por qué si $P \neq NP$, un lenguaje NP-completo no pertenece a $P$?

### j. ¿Cuándo se sospecha que un lenguaje de $NP$ está en $NPI$?

## 2. Sea $SMALL-SAT = \lbrace \phi \mid \phi \text{ es una fórmula booleana tal que...} \rbrace$. No tiene cuantificadores, está en la forma normal conjuntiva (o FNC), y existe una asignación de valores de verdad que la satisface en la que hay a lo sumo 3 variables con valor de verdad V. Probar que $\text{SMALL-SAT} \in P$. Comentario: una fórmula booleana sin cuantificadores está en la forma FNC si es una conjunción de disyunciones de variables o variables negadas, como es el caso, por ejemplo, de la fórmula $(x_1 \lor x_2) ∧ x_4 ∧ (\lnot x_3 \lor x_5 \lor x_6).$ Ayuda: Una MT que decida $\text{SMALL-SAT}$ debe contemplar asignaciones con cero, uno, dos y hasta tres valores de verdad verdadero.

## 3. Dados los dos lenguajes siguientes, (1) justificar por qué no estarían en $P$, (2) probar que están en $NP$, (3) justificar por qué sus complementos no estarían en $NP$:

### a. El problema del conjunto dominante de un grafo consiste en determinar si un grafo no dirigido tiene un conjunto dominante de vértices. Un subconjunto $D$ de vértices de un grafo $G$ es un conjunto dominante de $G$, sii todo vértice de $G$ fuera de $D$ es adyacente a algún vértice de $D$. El lenguaje que representa el problema es $\text{DOM-SET} = \lbrace (G, K) \mid \text{ G es un grafo ND y tiene un conjunto dominante de K vértices} \rbrace$.

### b. El problema de los grafos isomorfos consiste en determinar si dos grafos son isomorfos. Dos grafos son isomorfos si son idénticos salvo por la denominación de sus arcos. Por ejemplo, el grafo $G_1 = ( \lbrace 1, 2, 3, 4 \rbrace, \lbrace (1,2), (2,3), (3,4), (4,1) \rbrace )$ es isomorfo al grafo $G_2 = ( \lbrace 1, 2, 3, 4 \rbrace, \lbrace (1,2), (2,4), (4,3), (3,1) \rbrace)$. El lenguaje que representa el problema es $ISO = \lbrace (G_1, G_2) \mid G_1 \text{ y } G_2 \text{ son grafos isomorfos} \rbrace$.

## 4. Se prueba que $NP \subseteq EXP$. La prueba es la siguiente. Si $L \in NP$, entonces existe una MT $M$ que, para toda cadena de entrada $w$, verifica en tiempo $poly(|w|)$ si $w \in L$, con la ayuda de un certificado $x$ tal que $|x| \leq p(|w|)$. $p$ es un polinomio -, y de esta manera, se puede construir una MT $M'$ que decida en tiempo $exp(|w|)$ si $w \in L$, sin usar ninguna cadena adicional: $M'$ simplemente barre todos y cada uno de los certificados posibles $x$ de $w$. Se pide explicar por qué $M'$ efectivamente tarda tiempo $exp(|w|)$. Ayuda: como $|x| \leq p(|w|)$ y los símbolos de $x$ pertenecen a un alfabeto de $k$ símbolos, ¿cuántos certificados $x$ puede tener a lo sumo una cadena $w$?

## 5. Probar:

### a. Si los lenguajes $A$ y $B$ son tales que $A \neq \emptyset$, $A \neq \Sigma^*$ y $B \in P$, entonces $(A \cap B) \leq_p A$.

### b) Si $L_1 \in NPC$ y $L_2 \in NPC$, entonces $L_1 \leq_p L_2$ y $L_2 \leq_p L_1$.

### c) Si $L_1 \leq_p L_2$, $L_2 \leq_p L_1$, y $L_1 \in NPC$, entonces $L_2 \in NPC$.

### d) Si un lenguaje es $NPC$, entonces su complemento es $\text{CO-NPC}$, es decir, está en $\text{CO-NP}$ y todos los lenguajes de $\text{CO-NPC}$ se reducen polinomialmente a él. Ayuda: $L_1 \leq_p L_2$ sii $L_1^C \leq_p L_2^C$.

## 6. Sea el lenguaje $\text{SH-s-t} = \lbrace (G, s, t) \mid \text{ G es un grafo que tiene un camino de Hamilton del vértice s al vértice t} \rbrace$. Un grafo $G = (V, E)$ tiene un camino de Hamilton del vértice $s$ al vértice $t$ sii $G$ tiene un camino entre $s$ y $t$ que recorre todos los vértices restantes una sola vez. Probar que $\text{SH-s-t} \in NPC$. Ayuda: se sabe que $CH$, el lenguaje correspondiente al problema del circuito hamiltoniano, es $NPC$.

## 7. Probar que el lenguaje $FACT = \lbrace (N, M_1, M_2) \mid N \text{ tiene un divisor primo en el intervalo } [M_1, M_2] \rbrace$ está tanto en $NP$ como en $\text{CO-NP}$. Ayuda: Todo número natural $N$ se descompone de una única manera en factores primos, los cuales concatenados no ocupan más de $poly(|N|)$ símbolos.
