<h1 align="center">2024 - 1° fecha</h1>

## 1.

### a. ¿Cuándo un lenguaje es recursivamente enumerable y cuándo un lenguaje es recursivo?

### b. ¿Existen lenguajes recursivamente enumerables no recursivos? Dar un ejemplo.

### c. ¿Existen lenguajes no recursivamente enumerables? Dar un ejemplo.

## 2. Construir (dar sólo la idea general) una MT que acepte los pares de códigos de MT $(\langle M_1 \rangle, \langle M_2 \rangle)$ tales que la MT $M_1$ o la MT $M_2$ acepten la cadena vacía.

## 3. Se prueba que todos los lenguajes recursivamente enumerables se reducen al lenguaje $HP$, representante del problema de la detención. Explicar por qué, si $HP$ fuera recursivo, también lo serian todos los lenguajes recursivamente enumerables.

## 4. Justificar por qué la siguiente función $f$ no es una reducción del lenguaje $HP$ al lenguaje $HP^C$ (el complemento de $HP$): a todo par $(\langle M_1 \rangle, w)$, $f$ le asigna el par $(\langle M_2 \rangle, w)$, tal que $\langle M_2 \rangle$ es como $\langle M_1 \rangle$ salvo que sus estados finales están invertidos (es decir, donde aparece $q_A$ en $\langle M_1 \rangle$ aparece $q_R$ en $\langle M_2 \rangle$ y viceversa). Comentario: asumir que los pares $(\langle M_1 \rangle, w)$ siempre son sintácticamente correctos.

## 5.

### a. ¿Cuándo un lenguaje pertenece a la clase $P$ y cuándo un lenguaje pertenece a la clase $NP$?

### b. Dar un ejemplo de lenguaje en $NP$ que no estaría en $P$, y justificar por qué no estaría en $P$.

### c. Dar un ejemplo de lenguaje que no estaría en $NP$, y justificar por qué no estaría en $NP$.

## 6. Describir el método que estudiamos para poblar la clase de los lenguajes $NPC$, contando ya al menos con un lenguaje que pertenezca a dicha clase, y justificar por qué es correcto.

## 7.

### a. ¿Qué lenguajes se consideran tratables en la jerarquía espacial? Justificar por qué.

### b. Explicar por qué una MT que ocupa espacio $poly(n)$ puede tardar más que tiempo $poly(n)$.

### c. Dada una MT $M_1$ que ocupa espacio $S(n)$, explicar cómo se puede construir a partir de ella una MT $M_2$ que en espacio $S(n)$ imprima una cadena con $S(n)$ marcas $X$.

## 8.

### a. Especificar un programa que calcule el $mcd$, es decir el máximo común divisor de dos números enteros. Comentario: en la postcondición se puede usar la notación $mcd(x, y)$.

### b. Justificar por qué $(x > 0, y = x)$ no es una especificación correcta de un programa que debe devolver, en la variable de salida $y$, el valor de la variable de entrada $x$.

### c. El hecho de que un programa satisfaga la especificación $(x > 0, x > 0)$, ¿asegura que la aserción $x > 0$ se cumpla a lo largo de toda su ejecución? Justificar la respuesta.

## 9. Asumiendo que se cumple la fórmula de correctitud total $\langle p \rangle S \langle q \rangle$ indicar, justificando la respuesta, si se cumple cada uno de los siguientes enunciados:

### a. Si $S$ no termina, entonces su estado inicial no satisface $p$.

### b. Si $S$ termina en un estado que satisface $q$, entonces su estado inicial satisface $p$.

### c. Si $S$ termina en un estado que no satisface $q$, entonces su estado inicial no satisface $p$.

## 10. Probar mediante el método $H$, usando el invariante $p$, la fórmula de correctitud parcial $\lbrace p \rbrace \text{while ¬q do skip od} \lbrace q \rbrace$.

---

<h1 align="center">2025 - Ejemplo de examen</h1>

## 1. Probar que el conjunto $RE$ es cerrado con respecto a la operación de intersección $\cap$, es decir que para todo par de lenguajes $L_1, L_2 \in RE$, se cumple que $L_1 \cap L_2 \in RE$.

## 2. Sea $L_1$ un lenguaje generado con los símbolos del alfabeto $\Sigma_1$. Sea $f: \Sigma_1 \rightarrow \Sigma_2^*$ una función total computable, consistente en asignar a cada símbolo de $\Sigma_1$ una cadena de $\Sigma_2^*$. Y sea $L_2$ el lenguaje formado por las cadenas obtenidas de la aplicación de $f$ sobre las cadenas de $L_1$. Es decir que dado $L_1 = \lbrace w_1, w_2, \ldots \rbrace$, el lenguaje $L_2$ es $\lbrace f(w_1), f(w_2), \ldots \rbrace$, entendiendo que $f(w)$, con $w = w_1 w_2 \ldots w_n$ significa $f(w_1) f(w_2) \ldots f(w_n)$. Por ejemplo, si $abc \in L_1$, entonces $f(a) = 1$, $f(b) = 00$ y $f(c) = 101$, entonces $f(abc) = 100101 \in L_2$. Probar que si $L_1 \in R$, entonces $L_2 \in RE$. Ayuda: Construir una MT que reconozca $L_2$.

## 3. El problema $\text{K-CLIQUE}$ consiste en determinar si un grafo no orientado incluye un clique de tamaño $k$, es decir un subgrafo completo de $k$ vértices. El lenguaje que lo representa es $\text{K-CLIQUE} = \lbrace (G, k) \mid G \text{ es un grafo no orientado}, k > 0 \in \mathbb{N}, \text{G incluye un clique de tamaño } k \rbrace$. Probar que $\text{3-CLIQUE} \in P$, es decir, se puede determinar en tiempo deterministíco polinomial si un grafo no orientado incluye un triangulo (clique de tamaño 3).

## 4. El problema PARTICIÓN consiste en determinar si un conjunto finito de números naturales se puede partir en dos conjuntos $C_1$ y $C_2$, tales que la suma de los números de $C_1$ sea igual a la suma de los números de $C_2$. $\ldots$

## 5. $\ldots$

## 6. $\ldots$

---

<h1 align="center">2025 - 1° fecha</h1>

## 1. Definir cuándo un lenguaje pertenece a las siguientes clases y además dar un ejemplo de lenguaje de cada clase:

### a. $R$

### b. $RE - R$

### c. $\text{CO-RE} - R$

### d. $\mathcal{L} - (RE \cup \text{CO-RE})$

## 2. Sea $L_1$ un lenguaje de $R$ y $L_2$ un lenguaje de $RE$.

### a. Probar, construyendo una MT $M$ que $L_1 \cup L_2 \in RE$. Solo dar, claramente, la idea general de $M$.

### b. Dar un ejemplo de lenguaje $L_1$ de $R$ y un lenguaje $L_2$ de $RE$ tal que $L_1 \cup L_2 \notin R$.

## 3. En el marco de la computabilidad:

### a. ¿Qué significa que una prueba sea constructiva?

### b. ¿Por qué las pruebas de no pertenencia a $R$ o a $RE$ no pueden ser constructivas?

### c. ¿Qué técnicas existen para probar la no pertenencia a $R$ o a $RE$?

## 4. Indicar, justificando la respuesta, si se cumplen los siguientes enunciados, todos referidos al lenguaje $HP$:

### a. Si $L \notin RE$, entonces no existe una reducción de $L$ a $HP$.

### b. Si existe una reducción de $HP$ a un lenguaje $L$, entonces $L \in RE$.

### c. Si todos los lenguajes de $R$ se reducen a $HP$, entonces $R = RE$.

## 5. Definir cuándo un lenguaje (además, dar un ejemplo de lenguaje de cada clase):

### a. Pertenece a la clase $P$.

### b. Pertenece a la clase $NP$.

### c. Pertenecería a la clase $NPI$.

## 6. Probar la pertenencia a la clase $NP$ del lenguaje $PARTICIÓN$, definido como el conjunto $C$ de números naturales que se puede particionar en dos subconjuntos $C_1$ y $C_2$ tales que la suma de los elementos de $C_1$ coincide con la suma de los elementos de $C_2$. Comentario: se sabe que la suma de $k$ números se puede realizar en tiempo polinomial.

## 7. Indicar, justificando la respuesta, si se cumplen los siguientes enunciados, todos referidos al lenguaje $SAT$ (el lenguaje del problema de satisfactibilidad):

### a. Todos los lenguajes de $P$ se reducen polinomialmente a $SAT$.

### b. Si existe una reducción polinomial de $SAT$ a un lenguaje $L$, entonces $L \in NPC$.

### c. Si existe una reducción polinomial de $SAT$ a un lenguaje de $P$, entonces $P = NP$.

## 8. Responder:

### a. ¿Cuándo un programa es correcto parcialmente con respecto a una especificación?

### b. ¿Cuándo un programa es correcto totalmente con respecto a una especificación?

### c. ¿Por qué se hace la distinción entre correctitud parcial y correctitud total?

## 9. Especificar un programa que calcule la raíz cuadrada de un número $x$ que sea entero y mayor estricto que cero, y tal que al final, $x$ tenga el mismo valor que al inicio del programa.

## 10. Probar con el método $H$:

### a. $\lbrace x = X \land X > 0 \rbrace y := 2x \lbrace x = X \land y \geq 2 \rbrace$.

### b. $\lbrace true \rbrace \text{while true do skip od} \lbrace false \rbrace$

---

<h1 align="center">Desconocido</h1>

## 1. 

## 2.

## 3.

## 4.

## 5.

## 6.

## 7.

## 8.

## 9.

## 10.
