<h1 align="center">Trabajo Práctico 6</h1>

## 1. Presentamos en clase el lenguaje de las expresiones enteras: $$e :: 0 \mid 1 \mid x \mid (e_1 + e_2) \mid (e_1 \cdot e_2)$$ y comenzamos a probar por inducción estructural que para toda expresión $e$ se cumple: $C(e) = O(e) + 1$, es decir que el número de constantes o variables de la expresión $e$ es igual al número de operadores de la expresión $e$ más uno. Probamos las bases inductivas y el paso inductivo con $+$. Probar el paso inductivo con $\cdot$.

**Probar que $C(e) = O(e) + 1$ para toda expresión $e$**:

1. $C(e)$ es la cantidad de símbolos $0$, $1$ y $x$ que aparecen en la expresión $e$.
2. $O(e)$ es la cantidad de operadores $+$ y $\cdot$ que aparecen en la expresión $e$.
3. **Bases inductivas**:
   1. $C(0) = 1 + O(0) = 1 + 0 = 1$
   2. $C(1) = 1 + O(1) = 1 + 0 = 1$
   3. $C(x) = 1 + O(x) = 1 + 0 = 1$
4. **Paso inductivo respecto al operador $+$**:
   1. Suponemos que:
      1. $C(e_1) = O(e_1) + 1$
      2. $C(e_2) = O(e_2) + 1$
      3. para todas las expresiones $e_1$ y $e_2$.
   2. $C(e_1 + e_2) = C(e_1) + C(e_2) = (O(e_1) + 1) + (O(e_2) + 1) = O(e_1) + O(e_2) + 2$ (hipótesis inductiva)
   3. $O(e_1 + e_2) = O(e_1) + O(e_2) + 1$ (porque hay un operador $+$ adicional)
   4. Sumando 1 a ambos lados: $O(e_1 + e_2) + 1 = O(e_1) + O(e_2) + 2$
   5. Sustituyendo: $O(e_1 + e_2) + 1 = C(e_1 + e_2)$.
   6. Reordenando los términos: $C(e_1 + e_2) = O(e_1 + e_2) + 1$.
5. **Paso inductivo respecto al operador $\cdot$**:
   1. Suponemos que:
      1. $C(e_1) = O(e_1) + 1$
      2. $C(e_2) = O(e_2) + 1$
      3. para todas las expresiones $e_1$ y $e_2$.
   2. $C(e_1 \cdot e_2) = C(e_1) + C(e_2) = (O(e_1) + 1) + (O(e_2) + 1) = O(e_1) + O(e_2) + 2$. (hipótesis inductiva)
   3. $O(e_1 \cdot e_2) = O(e_1) + O(e_2) + 1$ (porque hay un operador $\cdot$ adicional)
   4. Sumando 1 a ambos lados: $O(e_1 \cdot e_2) + 1 = O(e_1) + O(e_2) + 2$
   5. Sustituyendo: $O(e_1 \cdot e_2) + 1 = C(e_1 \cdot e_2)$.
   6. Reordenando los términos: $C(e_1 \cdot e_2) = O(e_1 \cdot e_2) + 1$.

## 2. Sea otra vez el lenguaje $$e :: 0 \mid 1 \mid x \mid (e_1 + e_2) \mid (e_1 \cdot e_2)$$ y sea $var(e)$ el conjunto de las variables de la expresión $e$. Definir inductivamente $var(e)$. Ayuda: $var(0) = \emptyset$, $var(e_1 + e_2) = var(e_1) \cup var(e_2)$.

## 3. Supongamos que agregamos al lenguaje de programación visto en clase, la instrucción $\text{repeat S until B}$, con la semántica habitual. Informalmente: se ejecuta $S$, se evalúa $B$, si se cumple $B$ se termina la repetición, y si no se cumple $B$ se vuelve al comienzo. Definir formalmente dicha semántica. Comentario: puede ayudar revisar cómo definimos en clase la semántica formal del $while$.

## 4. Probar la sensatez de la siguiente regla de verificación: $$\frac{\lbrace p \rbrace S \lbrace q \rbrace, \lbrace p \rbrace S \lbrace r \rbrace}{\lbrace p \rbrace S \lbrace q \land r \rbrace}$$ Comentario: basarse en los ejemplos que vimos en clase.
