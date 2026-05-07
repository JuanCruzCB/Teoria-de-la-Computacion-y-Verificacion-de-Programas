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

<h1 align="center">???</h1>
