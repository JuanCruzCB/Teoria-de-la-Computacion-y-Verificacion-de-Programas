<h1 align="center">Trabajo Práctico 6</h1>

## 1. Presentamos en clase el lenguaje de las expresiones enteras: $$e :: 0 \mid 1 \mid x \mid (e_1 + e_2) \mid (e_1 \cdot e_2)$$ y comenzamos a probar por inducción estructural que para toda expresión $e$ se cumple: $C(e) = O(e) + 1$, es decir que el número de constantes o variables de la expresión $e$ es igual al número de operadores de la expresión $e$ más uno. Probamos las bases inductivas y el paso inductivo con $+$. Probar el paso inductivo con $\cdot$.

## 2. Sea otra vez el lenguaje $$e :: 0 \mid 1 \mid x \mid (e_1 + e_2) \mid (e_1 \cdot e_2)$$ y sea $var(e)$ el conjunto de las variables de la expresión $e$. Definir inductivamente $var(e)$. Ayuda: $var(0) = \emptyset$, $var(e_1 + e_2) = var(e_1) \cup var(e_2)$.

## 3. Supongamos que agregamos al lenguaje de programación visto en clase, la instrucción $\text{repeat S until B}$, con la semántica habitual. Informalmente: se ejecuta $S$, se evalúa $B$, si se cumple $B$ se termina la repetición, y si no se cumple $B$ se vuelve al comienzo. Definir formalmente dicha semántica. Comentario: puede ayudar revisar cómo definimos en clase la semántica formal del $while$.

## 4. Probar la sensatez de la siguiente regla de verificación: $$\frac{\lbrace p \rbrace S \lbrace q \rbrace, \lbrace p \rbrace S \lbrace r \rbrace}{\lbrace p \rbrace S \lbrace q \land r \rbrace}$$ Comentario: basarse en los ejemplos que vimos en clase.
