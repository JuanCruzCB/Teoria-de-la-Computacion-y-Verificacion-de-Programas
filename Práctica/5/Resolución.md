<h1 align="center">Trabajo Práctico 5</h1>

## 1. Se verificó en clase el programa del factorial de $x > 0$, con la especificación $(x > 0, y = x!)$.

### a. Justificar por qué esta especificación no es correcta.

La especificación no es correcta porque si bien se puede cumplir que $x > 0$ antes de iniciar el programa, éste mismo puede modificar el valor de $x$ durante su ejecución, lo que podría llevar a que $y \neq x!$ al final del programa.

El punto principal es que la $x$ de la postcondición se refiere al ÚLTIMO valor que tomó $x$ durante la ejecución del programa, y no al valor inicial que tenía.

Podría darse este caso, por ejemplo:

- Valor inicial: $x = 3$ y $3 > 0$ (la precondición es verdadera).
- Durante la ejecución, el programa podría modificar $x$ a $2$, luego a $1$, y finalmente a $0$.
- Al finalizar, $y$ podría ser igual a $6$, siendo $6 = 3!$, lo cual sería válido, pero como el valor final de $x$ es $0$, la postcondición $y = x!$ no se cumple, ya que $0! = 1$.

### b. Proponer una que sí lo sea y que además establezca que el valor de $x$ al final sea el mismo que al comienzo.

Propongo la especificación $(x = X \land X > 0, y = X! \land x = X)$, donde:

- $X$ es una variable lógica que representa el valor inicial de $x$.
- Por más que $x$ cambie de valor durante la ejecución del programa, el valor de la variable lógica $X$ se mantiene fijo.
- Al finalizar el programa se chequea que a) $y$ sea igual al factorial del valor inicial de $x$ (es decir, $X!$) y b) que $x$ no haya cambiado de valor en absoluto, ya que se chequea que $x$ sea igual a $X$ que como dijimos es el valor inicial de $x$.
- Por lo tanto, bajo esta especificación, si el programa factorial modifica la variable $x$ durante su ejecución de forma tal que al terminar la ejecución $x$ es distinto a su valor inicial, la postcondición no se cumple. Sin embargo, si modifica $x$ pero antes de terminar lo vuelve a modificar dandole el valor inicial, entonces la postcondición sí se cumple.

### c. ¿Podría agregarse a la especificación que el valor de $x$ no se altere a lo largo de todo el programa? Justificar.

No es posible agregar ni una precondición ni una postcondición que asegure que el valor de cualquier variable **nunca** se modifique en absoluto en toda la ejecución.

Esto se debe a que la Lógica de Hoare solo puede analizar el estado del programa **antes** de ejecutarlo y **después** de ejecutarlo, pero no puede garantizar nada de lo que pasa en el medio (durante la ejecución).

## 2. Asumiendo $\lbrace p \rbrace S \lbrace q \rbrace$, indicar en cada caso si vale lo afirmado. Justificar las respuestas:

Para este ejercicio es útil representar al significado de la correctitud parcial $\lbrace p \rbrace S \lbrace q \rbrace$ con una tabla de verdad que relacione el valor de $p$, el de $q$, y la terminación o no del programa $S$, que denoto $r$.

La correctitud parcial dice: "Si el estado inicial satisface $p$ y el programa $S$ termina, entonces el estado final satisface $q$". Esto se puede expresar como la implicación lógica $(p \land r) \rightarrow q$.

| $p$ | $q$ | $r$ | $(p \land r)$ | $(p \land r) \rightarrow q$ |
| --- | --- | --- | ------------- | --------------------------- |
| $V$ | $V$ | $V$ | $V$           | $V$                         |
| $V$ | $V$ | $F$ | $F$           | $V$                         |
| $V$ | $F$ | $V$ | $V$           | $F$                         |
| $V$ | $F$ | $F$ | $F$           | $V$                         |
| $F$ | $V$ | $V$ | $F$           | $V$                         |
| $F$ | $V$ | $F$ | $F$           | $V$                         |
| $F$ | $F$ | $V$ | $F$           | $V$                         |
| $F$ | $F$ | $F$ | $F$           | $V$                         |

El único caso donde la correctitud parcial no se cumple es cuando $p = V$, $q = F$, y $r = V$, es decir, cuando el estado inicial satisface $p$, el programa termina, pero el estado final no satisface $q$.

### a. Si $S$ termina en un estado que satisface $q$, entonces su estado inicial satisface $p$.

Tenemos $q = V$, $r = V$. Las filas de la tabla que cumplen esto son la primera y la quinta. En la primera fila, $p = V$ y la implicación es verdadera, pero en la quinta fila, $p = F$ y la implicación también es verdadera. Por lo tanto, no es cierto que si $S$ termina en un estado que satisface $q$, entonces su estado inicial satisface $p$, ya que puede pasar que $S$ termine en un estado que satisface $q$ pero el estado inicial no satisfaga $p$.

**No vale lo afirmado**.

### b. Si $S$ termina en un estado que no satisface $q$, entonces su estado inicial no satisface $p$.

Tenemos $q = F$, $r = V$. Las filas de la tabla que cumplen esto son la tercera y la séptima. En la tercera fila, $p = V$ y la implicación es falsa, pero en la séptima fila, $p = F$ y la implicación es verdadera. Por lo tanto sí es cierto si $S$ termina en un estado que no satisface $q$, entonces su estado inicial no satisface $p$.

**Vale lo afirmado**.

### c. Si $S$ no termina, entonces su estado inicial no satisface $p$.

Tenemos $r = F$. Mirando las filas 2, 4, 6 y 8, vemos que en la fila 2, $p = V$ y la implicación es verdadera, por lo tanto no es cierto que si $S$ no termina, entonces su estado inicial no satisface $p$, ya que puede pasar que $S$ no termine pero el estado inicial satisfaga $p$.

**No vale lo afirmado**.

### d. ¿Las respuestas en (a), (b) y (c) son las mismas considerando $\langle p \rangle S \langle q \rangle$?

$\langle p \rangle S \langle q \rangle$ se refiere a la correctitud total, que dice "Si el estado inicial satisface $p$, entonces el programa $S$ termina y el estado final satisface $q$".

Simbólicamente: $p \rightarrow (r \land q)$.

Reescribiendo la tabla de verdad:

| $p$ | $q$ | $r$ | $(r \land q)$ | $p \rightarrow (r \land q)$ |
| --- | --- | --- | ------------- | --------------------------- |
| $V$ | $V$ | $V$ | $V$           | $V$                         |
| $V$ | $V$ | $F$ | $F$           | $F$                         |
| $V$ | $F$ | $V$ | $F$           | $F$                         |
| $V$ | $F$ | $F$ | $F$           | $F$                         |
| $F$ | $V$ | $V$ | $V$           | $V$                         |
| $F$ | $V$ | $F$ | $F$           | $V$                         |
| $F$ | $F$ | $V$ | $F$           | $V$                         |
| $F$ | $F$ | $F$ | $F$           | $V$                         |

1. (a) Si $S$ termina en un estado que satisface $q$, entonces su estado inicial satisface $p$.
   1. Tenemos $q = V$, $r = V$. Filas 1 y 5. Lo afirmado no se cumple porque puede pasar que $S$ termine en un estado que satisface $q$ pero el estado inicial no satisfaga $p$ (fila 5).
   2. **No vale lo afirmado**.
2. (b) Si $S$ termina en un estado que no satisface $q$, entonces su estado inicial no satisface $p$.
   1. Tenemos $q = F$, $r = V$. Filas 3 y 7. Lo afirmado se cumple porque si $S$ termina en un estado que no satisface $q$, entonces el estado inicial no satisface $p$ (fila 7).
   2. **Vale lo afirmado**.
3. (c) Si $S$ no termina, entonces su estado inicial no satisface $p$.
   1. Tenemos $r = F$. Filas 2, 4, 6 y 8. Viendo las filas 6 y 8 que son las que cumplen la implicación, vemos que en ambos casos el estado inicial no satisface $p$, por lo tanto lo afirmado se cumple, a diferencia de la correctitud parcial, donde no se cumple.
   2. **Vale lo afirmado**.

## 3. Indicar en cada caso si vale lo afirmado. Justificar las respuestas:

### a. Se cumple $\lbrace x = 0 \rbrace \text{while } z = 0 \text{ do } z := 0 \text{ od} \lbrace x = 0 \rbrace$.

1. Si al iniciar el programa se cumple $x = 0$ y $z = 0$ se entra en loop infinito. Tenemos $p = V$ y $r = F$. Filas 2 y 4 de la tabla de correctitud parcial. En ambas filas la implicación es verdadera ya sea que $q$ sea $V$ o $F$.
2. Si al inciar el programa se cumple $x = 0$ y $z \neq 0$ no se entra en loop infinito. Como el programa termina, se puede evaluar $q$ al finalizar el programa, y como el programa no modifica $x$, entonces $q$ se cumple. Tenemos $p = V$, $r = V$, y $q = V$. Fila 1 de la tabla de correctitud parcial, donde la implicación es verdadera.
3. Si al iniciar el programa se cumple $x \neq 0$ y $z = 0$ se entra en loop infinito. Tenemos $p = F$ y $r = F$. Filas 6 y 8 de la tabla de correctitud parcial. En ambas filas la implicación es verdadera ya sea que $q$ sea $V$ o $F$.
4. Si al iniciar el programa se cumple $x \neq 0$ y $z \neq 0$ no se entra en loop infinito. Como el programa termina, se puede evaluar $q$ al finalizar el programa, y como el programa no modifica $x$, entonces $q$ no se cumple. Tenemos $p = F$, $r = V$, y $q = F$. Fila 7 de la tabla de correctitud parcial, donde la implicación es verdadera.

Como es imposible que la implicación de la C.P sea falsa, vale lo afirmado.

### b. Se cumple $\langle x = 0 \rangle \text{while } z = 0 \text{ do } z := 0 \text{ od} \langle x = 0 \rangle$.

1. Si al iniciar el programa se cumple $x = 0$ y $z = 0$ se entra en loop infinito. Tenemos $p = V$ y $r = F$. Filas 2 y 4 de la tabla de correctitud total. En ambas filas la implicación es falsa ya sea que $q$ sea $V$ o $F$.

Como se encontró un caso donde la implicación de la C.T es falsa, no vale lo afirmado.

### c. Si se cumple $\lbrace p_1 \land p_2 \rbrace S \lbrace q_1 \land q_2 \rbrace$, entonces $\lbrace p_1 \rbrace S \lbrace q_1 \rbrace$ o bien $\lbrace p_2 \rbrace S \lbrace q_2 \rbrace$.

Contraejemplo:

1. Sea $S$ el programa que no hace nada (es solo una sentencia `skip`).
2. Sea $p_1$ la precondición $x = 0$, y $p_2$ la precondición $x = 1$.
3. Sean $q_1 = F$ y $q_2 = F$.
4. Claramente $(p_1 \land p_2) = F$ porque $x$ no puede valer $0$ y $1$ al mismo tiempo.
5. Obviamente $(q_1 \land q_2) = F$ porque ambos son falsos.
6. Entonces tenemos $\lbrace F \rbrace S \lbrace F \rbrace$, lo cual es válido porque si la precondición de una implicación es falsa, la implicación es verdadera.
7. Sin embargo, si $p_1$ es $x = 0$, entonces $\lbrace p_1 \rbrace S \lbrace q_1 \rbrace$ es $\lbrace x = 0 \rbrace S \lbrace F \rbrace$, lo cual no es válido porque si la precondición se cumple, el programa termina, pero la postcondición no se cumple.
8. En el otro caso, si $p_2$ es $x = 1$, entonces $\lbrace p_2 \rbrace S \lbrace q_2 \rbrace$ es $\lbrace x = 1 \rbrace S \lbrace F \rbrace$, lo cual no es válido por la misma razón que el caso anterior.
9. Por lo tanto $\lbrace p_1 \land p_2 \rbrace S \lbrace q_1 \land q_2 \rbrace$ es válido, pero ni $\lbrace p_1 \rbrace S \lbrace q_1 \rbrace$ ni $\lbrace p_2 \rbrace S \lbrace q_2 \rbrace$ son válidos.
10. No vale lo afirmado.

## 4. Probar por medio del método H las fórmulas de correctitud parcial siguientes, relacionadas respectivamente a programas que calculan el valor absoluto de un número entero y el producto de dos números naturales:

### a. $\lbrace x = X \rbrace \text{if } x > 0 \text{ then } y := x \text{ else } y := -x \rbrace \lbrace y = |X| \rbrace$, siendo $|X|$ el valor absoluto de $X$.

1. Se probará la terna de Hoare usando principalmente la regla del if.
2. Probar **$\lbrace p \land B \rbrace S_1 \lbrace q \rbrace$**:
   1. $\lbrace x = X \land x > 0 \rbrace y := x \lbrace y = |X| \rbrace$ (COND)
   2. $\lbrace x = |X| \rbrace y := x \lbrace y = |X| \rbrace$ (ASI)
   3. $x = X \land x > 0$
   4. $\Rightarrow X > 0$
   5. $\Rightarrow X = |X|$
   6. $\Rightarrow x = |X|$
   7. Conclusión: $(x = X \land x > 0) \rightarrow (x = |X|)$
   8. **$\lbrace x = X \land x > 0 \rbrace y := x \lbrace y = |X| \rbrace$** (CONS)
3. Probar **$\lbrace p \land \neg B \rbrace S_2 \lbrace q \rbrace$**:
   1. $\lbrace x = X \land \neg (x > 0) \rbrace y := -x \lbrace y = |X| \rbrace$ (COND)
   2. $\lbrace x = X \land x \leq 0 \rbrace y := -x \lbrace y = |X| \rbrace$ (MAT)
   3. $\lbrace -x = |X| \rbrace y := -x \lbrace y = |X| \rbrace$ (ASI)
   4. $x = X \land \neg (x > 0)$
   5. $\Rightarrow x = X \land x \leq 0$
   6. $\Rightarrow X \leq 0$
   7. $\Rightarrow -X = |X|$
   8. $\Rightarrow -x = |X|$
   9. Conclusión: $(x = X \land \neg (x > 0)) \rightarrow (-x = |X|)$
   10. **$\lbrace x = X \land \neg (x > 0) \rbrace y := -x \lbrace y = |X| \rbrace$** (CONS)
4. Finalmente:
   1. $\lbrace x = X \land x > 0 \rbrace y := x \lbrace y = |X| \rbrace$
   2. $\lbrace x = X \land \neg (x > 0) \rbrace y := -x \lbrace y = |X| \rbrace$
   3. **$\lbrace x = X \rbrace \text{if } x > 0 \text{ then } y := x \text{ else } y := -x \rbrace \lbrace y = |X| \rbrace$** (1, 2, COND)

### b. $\lbrace x \geq 0 \land y \geq 0 \rbrace prod := 0; k := y; \text{while k > 0 do } prod := prod + x; k := k - 1; od \lbrace prod = x.y \rbrace$

1. Elementos:
   1. Precondición: $p$ es $(x \geq 0 \land y \geq 0)$
   2. Postcondición: $prod = x \cdot y$
   3. La condición del while $B$ es $k > 0$
2. Se debe hallar un invariante $i$ que sea verdadero antes de entrar al while, que sea verdadero en cada iteración del while, y que sea verdadero al salir del while. Analizando el programa se pueden notar varias cosas:
   1. $y$ es la cantidad total de veces que queremos sumar $x$.
   2. $k$ es la cantidad de veces que aún falta sumar $x$. Siempre vale $y$ al inicio del programa, y siempre vale $0$ al finalizar el programa, porque justamente una vez vale $0$ se sale del loop. Además, se puede ver claramente que $k \geq 0$ siempre, porque empieza siendo igual a $y$ que es mayor o igual a $0$, y al salir del loop obviamente vale $0$, por lo que se cumple trivialmente que $k$ siempre es mayor o igual a $0$.
   3. $y - k$ es la cantidad de veces que ya se sumó $x$.
   4. Como en cada iteración del while se le suma $x$ a $prod$, entonces $prod$ es igual a $x$ multiplicado por la cantidad de veces que ya se sumó $x$, es decir, $prod = x \cdot (y - k)$.
   5. Por lo tanto, un invariante posible es $i \equiv prod = x \cdot (y - k) \land k \geq 0$.
3. Probar $p \rightarrow i$ para las primeras dos sentencias antes de entrar al while: **$\lbrace x \geq 0 \land y \geq 0 \rbrace prod := 0; k := y; \lbrace prod = x \cdot (y - k) \land k \geq 0 \rbrace$**
   1. $\lbrace prod = x \cdot (y - y) \land y \geq 0 \rbrace k := y; \lbrace prod = x \cdot (y - k) \land k \geq 0 \rbrace$ (ASI)
   2. $\lbrace prod = 0 \land y \geq 0 \rbrace k := y; \lbrace prod = x \cdot (y - k) \land k \geq 0 \rbrace$ (MAT)
   3. $\lbrace 0 = 0 \land y \geq 0 \rbrace prod := 0; \lbrace prod = 0 \land y \geq 0\rbrace$ (ASI)
   4. $\lbrace y \geq 0 \rbrace prod := 0; \lbrace prod = 0 \land y \geq 0 \rbrace$ (MAT)
   5. $\lbrace y \geq 0 \rbrace prod := 0; k := y; \lbrace prod = x \cdot (y - k) \land k \geq 0 \rbrace$ (4, 2, SEC)
   6. Se reemplaza la precondición del paso 5 por otra precondición que la implique, por la regla CONS: $(x \geq 0 \land y \geq 0) \rightarrow y \geq 0$ trivialmente verdadero porque $(q \land p) \rightarrow p$ es una tautología.
   7. **$\lbrace x \geq 0 \land y \geq 0 \rbrace prod := 0; k := y; \lbrace prod = x \cdot (y - k) \land k \geq 0 \rbrace$** (CONS)
4. Probar $i \land B \rightarrow i$: **$\lbrace prod = x \cdot (y - k) \land k \geq 0 \land k > 0 \rbrace prod := prod + x; k := k - 1; \lbrace prod = x \cdot (y - k) \land k \geq 0 \rbrace$**.
   1. $\lbrace prod = x \cdot (y - (k - 1)) \land k - 1 \geq 0 \rbrace k := k - 1; \lbrace prod = x \cdot (y - k) \land k \geq 0 \rbrace$ (ASI)
   2. $\lbrace prod = x \cdot (y - k + 1) \land k - 1 \geq 0 \rbrace k := k - 1; \lbrace prod = x \cdot (y - k) \land k \geq 0 \rbrace$ (MAT)
   3. $\lbrace prod + x = x \cdot (y - k + 1) \land k - 1 \geq 0 \rbrace prod := prod + x; \lbrace prod = x \cdot (y - k + 1) \land k - 1 \geq 0 \rbrace$ (ASI)
   4. $\lbrace prod = x \cdot (y - k + 1) - x \land k - 1 \geq 0 \rbrace prod := prod + x; \lbrace prod = x \cdot (y - k + 1) \land k - 1 \geq 0 \rbrace$ (MAT)
   5. $\lbrace prod = x \cdot (y - k + 1) - x \land k - 1 \geq 0 \rbrace prod := prod + x; k := k - 1; \lbrace prod = x \cdot (y - k) \land k \geq 0 \rbrace$ (4, 2, SEC)
   6. $\lbrace prod = x \cdot (y - k) \land k - 1 \geq 0 \rbrace prod := prod + x; k := k - 1; \lbrace prod = x \cdot (y - k) \land k \geq 0 \rbrace$ (MAT)
   7. Se reemplaza la precondición del paso 6 por otra precondición que la implique, por la regla CONS: $(prod = x \cdot (y - k) \land k \geq 0 \land k > 0) \rightarrow (prod = x \cdot (y - k) \land k - 1 \geq 0)$:
      1. $k > 0 \Rightarrow k - 1 \geq 0$
      2. $(prod = x \cdot (y - k) \land k \geq 0 \land k > 0) \Rightarrow (prod = x \cdot (y - k) \land k - 1 \geq 0)$
   8. **$\lbrace prod = x \cdot (y - k) \land k \geq 0 \land k > 0 \rbrace prod := prod + x; k := k - 1; \lbrace prod = x \cdot (y - k) \land k \geq 0 \rbrace$** (CONS)
5. Probar $i \land \lnot B \rightarrow prod = x \cdot y$: **$(prod = x \cdot (y - k) \land k \geq 0 \land \neg (k > 0))  \rightarrow prod = x \cdot y$**.
   1. $(prod = x \cdot (y - k) \land k \geq 0 \land \lnot (k > 0))$
   2. $\Rightarrow (prod = x \cdot (y - k) \land k \geq 0 \land k \leq 0)$
   3. $\Rightarrow (prod = x \cdot (y - k) \land k = 0)$
   4. $\Rightarrow (prod = x \cdot y \land k = 0)$
   5. $\Rightarrow (prod = x \cdot y)$
   6. Conclusión: **$(prod = x \cdot (y - k) \land k \geq 0 \land \neg (k > 0))  \rightarrow prod = x \cdot y$**.
6. Finalmente encadenamos todo:
   1. $\lbrace x \geq 0 \land y \geq 0 \rbrace prod := 0; k := y; \lbrace i \rbrace$ (probado en el paso 3)
   2. $\lbrace i \land k > 0 \rbrace prod := prod + x; k := k - 1; \lbrace i \rbrace$ (probado en el paso 4)
   3. $\lbrace i \rbrace \text{while } k > 0 \text{ do } prod := prod + x; k := k - 1 \text{ od } \lbrace i \land k \leq 0 \rbrace$ (REP)
   4. $\lbrace x \geq 0 \land y \geq 0 \rbrace prod := 0; k := y; \text{while } k > 0 \text{ do } prod := prod + x; k := k - 1 \text{ od } \lbrace i \land k \leq 0 \rbrace$ (1, 3, SEC)
   5. $i \land k \leq 0 \rightarrow prod = x \cdot y$ (probado en el paso 5)
   6. $\lbrace x \geq 0 \land y \geq 0 \rbrace prod := 0; k := y; \text{while } k > 0 \text{ do } prod := prod + x; k := k - 1 \text{ od } \lbrace prod = x \cdot y \rbrace$ (4, 5, CONS)

## 5. Se verificó en clase, usando el método H: $\lbrace x \geq 0 \land y > 0 \rbrace S_{div} :: q := 0; r := x; \text{while } r \geq y \text{ do } r := r - y; q := q + 1 \text{ od} \lbrace x = q \cdot y + r \land 0 \leq r < y \rbrace$ siendo $S_{div}$ un programa que calcula por restas sucesivas la división entera de $x$ sobre $y$ en $q$, dejando el resto en $r$. Se pide ahora probar en $H$: $\lbrace x > 0 \land y = 0 \rbrace S_{div} \lbrace false \rbrace$ que significa que el programa $S_{div}$ no termina a partir de la precondición $(x > 0 \land y = 0)$.

$\ldots$

## 6. Probar la terminación del programa planteado en el ejercicio 4.b, es decir: $\langle x \geq 0 \land y \geq 0 \rangle S_{prod} :: prod := 0; k := y; \text{while } k > 0 \text{ do } prod := prod + x; k := k - 1 \text{ od } \langle true \rangle$. Ayuda: Notar que $k$ se decrementa en cada iteración y que se mantiene siempre mayor o igual que cero.

Para probar la correctitud total de una terna de Hoare, se debe probar la correctitud parcial y además que el programa termina. En el ejercicio 4.b ya se demostró la parcial, por lo que ahora solo falta probar la terminación.

Para probar la terminación, se debe hallar una función variante $f$ que asegure que el número de iteraciones del bucle es finito, ergo que el programa termina. La función debe cumplir dos condiciones: a) decrecer en cada iteración del bucle b) tener un límite inferior → no puede decrecer infinitamente.

Se observó en el ejercicio 4.b que $k$ es la variable que controla cuándo el bucle termina, y además que siempre decrece en una unidad entera en cada iteración del bucle. Además, por el invariante que se encontró, se sabe que siempre $k \geq 0$. Por lo tanto, una función variante posible es $f(k) = k$, porque $f$ decrece en cada iteración del bucle, y además tiene un límite inferior que es $0$, ya que $k$ siempre es mayor o igual a $0$.

Verificamos las dos condiciones de la función variante $f(k) = k$:

1. Acotación inferior: como se sabe que $k \geq 0$ siempre, entonces $f(k) \geq 0$, por lo que $f$ tiene un límite inferior.
2. Decrecimiento: en cada iteración se ejecuta la instrucción $k := k - 1$. Como la función variante es $f(k) = k$, luego de una iteración se tiene $f'(k) = k - 1$. Como $k - 1 < k$ para cualquier $k$, entonces $f'(k) < f(k)$, por lo que $f$ decrece en cada iteración del bucle.

Como existe una función variante $f$ que está acotada inferiormente y decrece estrictamente en cada iteración, el bucle ejecuta una cantidad finita de iteraciones. Por lo tanto, el programa termina.

Dado que en el ejercicio 4.b ya se probó la correctitud parcial y ahora se probó la terminación, se sigue que el programa es totalmente correcto.
