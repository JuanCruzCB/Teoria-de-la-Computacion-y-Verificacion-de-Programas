<h1 align="center">Trabajo Práctico 4</h1>

## 1. Responder breve y claramente:

### a. ¿Por qué en la complejidad espacial se utilizan MT con una cinta de entrada de sólo lectura?

### b. ¿Por qué si una MT tarda tiempo $poly(n)$ entonces ocupa espacio $poly(n)$, y si ocupa espacio $poly(n)$ puede llegar a tardar tiempo $exp(n)$?

### c. ¿Por qué los lenguajes de la clase $LOGSPACE$ son tratables?

## 2. Describir la idea general de una MT $M$ que:

### a. Decida el lenguaje $L = \lbrace a^n b^n \mid n \geq 1 \rbrace$ en espacio logarítmico. Ayuda: basarse en el ejemplo mostrado en la clase 7.

### b. Decida el lenguaje $SAT$ en espacio polinomial. Ayuda: la generación y la evaluación de una asignación de valores de verdad se pueden efectuar en tiempo polinomial.

## 3. Probar que $NP \subseteq PSPACE$ de dos maneras:

### a. Usando que todos los lenguajes de $NP$ se reducen polinomialmente a $SAT$. Ayuda: tener en cuenta el resultado del ejercicio 1.2.b.

### b. Usando que si un lenguaje $L$ pertenece a $NP$, entonces existe una MT $M_1$ capaz de verificar en tiempo $poly(|w|)$ si una cadena $w$ pertenece a $L$, con la ayuda de un certificado $x$ de tamaño $poly(|w|)$. Ayuda: con dicha hipótesis, probar que existe una MT $M_2$ que decide $L$ en espacio $poly(|w|)$ sin la ayuda de ningún certificado.

## 4. Supongamos que existe una MT $M$ de tiempo polinomial que, dado un grafo $G$, devuelve un circuito de Hamilton de $G$ si existe o responde no si no existe. Describir la idea general de una MT $M'$ que, utilizando $M$, decida en tiempo polinomial si un grafo $G$ tiene un circuito de Hamilton. Ayuda: basarse en el ejemplo mostrado en la clase 7 con $FSAT$ y $SAT$.

## 5. Probar que si se puede encontrar en tiempo $poly(n)$ un circuito de Hamilton mínimo de un grafo completo ponderado $G$, entonces también se puede decidir en tiempo $poly(n)$ si $G$ tiene un circuito de Hamilton cuyos arcos suman $\leq B$.
