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

### a. Si $S$ termina en un estado que satisface $q$, entonces su estado inicial satisface $p$.

### b. Si $S$ termina en un estado que no satisface $q$, entonces su estado inicial no satisface $p$.

### c. Si $S$ no termina, entonces su estado inicial no satisface $p$.

### d. ¿Las respuestas en (a), (b) y (c) son las mismas considerando $\langle p \rangle S \langle q \rangle$?

## 3. Indicar en cada caso si vale lo afirmado. Justificar las respuestas:

### a. Se cumple $\lbrace x = 0 \rbrace \text{while } z = 0 \text{ do } z := 0 \text{ od} \lbrace x = 0 \rbrace$.

### b. Se cumple $\langle x = 0 \rangle \text{while } z = 0 \text{ do } z := 0 \text{ od} \langle x = 0 \rangle$.

### c. Si se cumple $\lbrace p_1 \land p_2 \rbrace S \lbrace q_1 \land q_2 \rbrace$, entonces $\lbrace p_1 \rbrace S \lbrace q_1 \rbrace$ o bien $\lbrace p_2 \rbrace S \lbrace q_2 \rbrace$.

## 4. Probar por medio del método H las fórmulas de correctitud parcial siguientes, relacionadas respectivamente a programas que calculan el valor absoluto de un número entero y el producto de dos números naturales:

### a. $\lbrace x = X \rbrace \text{if } x > 0 \text{ then } y := x \text{ else } y := -x \rbrace \lbrace y = |X| \rbrace$, siendo $|X|$ el valor absoluto de $X$.

### b. $\lbrace x \geq 0 \land y \geq 0 \rbrace \\ \text{prod := 0; k := y; while k > 0 do prod := prod + x; k := k - 1 od} \\ \lbrace prod = x.y \rbrace$.

## 5. Se verificó en clase, usando el método H: $\lbrace x \geq 0 \land y > 0 \rbrace \\ S_{div} :: q := 0; r := x; \text{while } r \geq y \text{ do } r := r - y; q := q + 1 \text{ od} \\ \lbrace x = q \cdot y + r \land 0 \leq r < y \rbrace$ siendo $S_{div}$ un programa que calcula por restas sucesivas la división entera de $x$ sobre $y$ en $q$, dejando el resto en $r$. Se pide ahora probar en $H$: $\lbrace x > 0 \land y = 0 \rbrace S_{div} \lbrace false \rbrace$ que significa que el programa $S_{div}$ no termina a partir de la precondición $(x > 0 \land y = 0)$.

## 6. Probar la terminación del programa planteado en el ejercicio 4.b, es decir: $\langle x \geq 0 \land y \geq 0 \rangle \\ S_{prod} :: prod := 0; k := y; \text{while } k > 0 \text{ do } prod := prod + x; k := k - 1 \text{ od } \\ \langle true \rangle$. Ayuda: Notar que $k$ se decrementa en cada iteración y que se mantiene siempre mayor o igual que cero.
