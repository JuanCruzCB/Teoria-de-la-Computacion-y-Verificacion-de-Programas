<h1 align="center">Resumen segundo parcial<h1>

## Conceptos básicos

### Validación vs verificación

La **validación** es una actividad **informal** que se realiza para comprobar que el software cumple con los requisitos del cliente, mientras que la **verificación** es una actividad **formal** que se realiza para comprobar que el software cumple con los requisitos especificados.

### Especificación vs programa

La **especificación** es una **descripción** detallada de lo que el software debe hacer, mientras que el **programa** es la **implementación** concreta del software que se ejecuta en una computadora.

### Formas de verificación

- **Semántica**: se usa la semántica de las instrucciones del lenguaje.
- **Sintáctica**: se usan axiomas y reglas de un método deductivo → Lógica de Hoare.

---

## Lógica de Hoare

### Definiciones

- **Terna de hoare**: $\lbrace p \rbrace C \lbrace q \rbrace$
  - $p$ es la precondición.
  - $C$ es el programa o fragmento de código a verificar.
  - $q$ es la postcondición.
- **Precondición**: $p$
  - Es un predicado que se asume verdadero antes de ejecutar el programa.
- **Postcondición**: $q$
  - Es un predicado que se asume verdadero después de ejecutar el programa.
- **Especificación**: $(p, q)$
  - Es el par de precondición y postcondición.
- **Estado**: $\sigma$
  - Es una función que asigna a toda variable un valor. Por ejemplo, $\sigma(x) = 1$, $\sigma(y) = 2$, etc.
- **Satisfacción**:
  - Un estado $\sigma$ satisface a un predicado $p$, denotado $\sigma \models p$, si y solo si $p$ es verdadero cuando se evalúa con los valores asignados por $\sigma$ a sus variables.
  - Por ejemplo, si $p$ es $x < y$ y $\sigma(x) = 1$, $\sigma(y) = 2$, entonces $\sigma \models p$ porque $1 < 2$ es verdadero.
- **Correctitud**:
  - Un programa $S$ es correcto con respecto a una especificación $(p, q)$, denotado $\lbrace p \rbrace S \lbrace q \rbrace$, si y solo si para todo estado $\sigma$, si $\sigma \models p$ entonces $S$ ejecutado a partir de $\sigma$ se detiene en un estado $\sigma'$ tal que $\sigma' \models q$.
  - Si desde $\sigma_0$ se ejecuta $S$ y no alcanza un estado $\sigma_0'$ dentro de $q$ entonces se cumple $\lbrace p \rbrace S \lbrace q \rbrace$ porque si $\sigma \nvDash q$, $\lbrace p \rbrace S \lbrace q \rbrace$ es trivialmente verdadero.

### Lenguaje de programación (programas con while):

- Instrucciones:
  - $S :: x := e$
  - $S :: S_1; S_2$
  - $S :: \text{if b then } S_1 \text{ else } S_2 \text{ fi}$
  - $S :: \text{while B do } S_1 \text{ od}$
- Expresiones de tipo entero:
  - $e :: n$
  - $e :: x$
  - $e :: (e_1 + e_2)$
  - $e :: (e_1 - e_2)$
  - $e :: (e_1 \cdot e_2)$
  - Donde $n$ es una constante entera y $x$ es una variable entera.
- Expresiones de tipo booleano:
  - $B :: true$
  - $B :: false$
  - $B :: (e_1 = e_2)$
  - $B :: (e_1 < e_2)$
  - $\ldots$
  - $B :: \lnot B_1$
  - $B :: (B_1 \lor B_2)$
  - $B :: (B_1 \land B_2)$
  - $\ldots$

### Lenguaje de especificación (lógica de predicados):

- $p :: true$
- $p :: false$
- $p :: (e_1 = e_2)$
- $p :: (e_1 < e_2)$
- $\ldots$
- $p :: \lnot p$
- $p :: (p_1 \lor p_2)$
- $p :: (p_1 \land p_2)$
- $\ldots$
- $p :: \exists x: p$
- $p :: \forall x: p$

### Axiomática y reglas

#### Axioma de la asignación (ASI)

- $\lbrace p[x | e] \rbrace x := e \lbrace p \rbrace$
- Se lee de derecha a izquierda: si luego de ejecutar $x := e$ vale $p$ en términos de $x$, entonces antes de ejecutar $x := e$ valía $p$ en términos de $e$.
- Por ejemplo:
  - $\lbrace ? \rbrace x := x + 1 \lbrace x \geq 0 \rbrace$
  - $\lbrace x \geq 0[x | x + 1] \rbrace x := x + 1 \lbrace x \geq 0 \rbrace$
  - $\lbrace x + 1 \geq 0 \rbrace x := x + 1 \lbrace x \geq 0 \rbrace$
  - Es decir, si luego de $x := x + 1$ vale $x \geq 0$, entonces antes de $x := x + 1$ valía $x + 1 \geq 0$.

#### Regla de la secuencia (SEC)

- $\frac{\lbrace p \rbrace S_1 \lbrace r \rbrace, \lbrace r \rbrace S_2 \lbrace q \rbrace}{\lbrace p \rbrace S_1; S_2 \lbrace q \rbrace}$
- El predicado $r$ actúa como un nexo entre $S_1$ y $S_2$ y luego se descarta, no se propaga.
- Se puede generalizar a $n$ instrucciones.

#### Regla del condicional (COND)

- $\frac{\lbrace p \land B \rbrace S_1 \lbrace q \rbrace, \lbrace p \land \lnot B \rbrace S_2 \lbrace q \rbrace}{\lbrace p \rbrace \text{ if B then } S_1 \text{ else } S_2 \text{ fi} \lbrace q \rbrace}$
- Formula un modo de verificar una selección condicional fijando un único punto de entrada y un único punto de salida, correspondientes a $p$ y $q$ respectivamente.

#### Regla de la repetición (REP)

- $\frac{\lbrace p \land B \rbrace S \lbrace p \rbrace}{\lbrace p \rbrace \text{ while B do } S \text{ od} \lbrace p \land \lnot B \rbrace}$
- $p$ se define en términos de las variables del programa $S$.
- $p$ es un predicado que vale antes y después de toda iteración, es decir, es un **invariante**.
- La regla NO asegura que el while termine.
- Si $p$ vale al comienzo del bucle y mientras vale $B$ el cuerpo $S$ preserva $p$, entonces por razonamiento inductivo $p$ vale al terminar el bucle.

#### Regla de la repetición con terminación (REP\*)

- $\frac{\langle p \land B \rangle S \langle p \rangle, \langle p \land B \land t = Z \rangle S \langle t < Z \rangle, p \rightarrow t \geq 0}{\langle p \rangle \text{ while B do } S \text{ od} \langle p \land \lnot B \rangle}$
- Permite probar además la terminación del while. Se basa en un predicado invariante $p$ y una función variante $t$ que es entera y está definida, como el invariante, en términos de las variables del programa.
- Se le agregan dos premisas a REP y se reemplazan las llaves por corchetes angulares.
- En la segunda premisa, $t$ se decrementa en cada iteración.
- $Z$ es una variable lógica, no aparece en $p$, $B$, $t$ ni en $S$.
- El objetivo de $Z$ es fijar el valor de $t$ antes de ejecutar $S$.
- En la tercera premisa, $t$ se mantiene menor o igual a cero a lo largo de todo el bucle.
- Así, el bucle debe necesariamente terminar, porque en los números naturales no hay cadenas descendentes infinitas.

#### Regla de la consecuencia (CONS)

- $\frac{p \rightarrow p_1, \lbrace p_1 \rbrace S \lbrace q_1 \rbrace, q_1 \rightarrow q}{\lbrace p \rbrace S \lbrace q \rbrace}$
- Se puede reemplazar $p_1$ por un predicado $p$ que lo implique.
- Se puede reemplazar $q_1$ por un predicado $q$ al que implique.
- Permite reforzar precondiciones y debilitar postcondiciones:
  - De $\lbrace x > 0 \rbrace S \lbrace x = 0 \rbrace$ y $x > 5 \rightarrow x > 0$ se deduce $\lbrace x > 5 \rbrace S \lbrace x = 0 \rbrace$.
  - De $\lbrace true \rbrace S \lbrace x = y + 1 \rbrace$ y $x = y + 1 \rightarrow x > y$ se deduce $\lbrace true \rbrace S \lbrace x > y \rbrace$.
- La regla no depende del lenguaje de programación si no del dominio semántico. Es una regla semántica más que sintáctica.
- Permite usar todos los axiomas del dominio semántico, como pueden ser los números enteros.

### Separación de la prueba del while en dos

- Si bien la regla REP\* permite probar tanto la correctitud parcial como la terminación de un while, es recomendable separar la prueba en dos partes:
  - Primero se prueba $\lbrace p \rbrace S \lbrace q \rbrace$ con REP para asegurar la invariancia de $p$.
  - Luego se prueba $\langle p \rangle S \langle true \rangle$ con REP\* para asegurar la terminación del bucle.
  - La primer prueba se lee: "Si $S$ termina a partir de $p$, lo hace en $q$".
  - La segunda prueba se lee: "$S$ termina a partir de $p$".
  - Las dos pruebas puestas juntas se leen: "$S$ termina a partir de $p$ y lo hace en $q$".

### Composicionalidad

- El método de prueba presentado es **composicional**: dado un programa $S$, compuesto por subprogramas $S_1, S_2, \ldots, S_n$, que valga la fórmula $\lbrace p \rbrace S \lbrace q \rbrace$, depende únicamente de que valgan las fórmulas $\lbrace p_1 \rbrace S_1 \lbrace q_1 \rbrace$, $\lbrace p_2 \rbrace S_2 \lbrace q_2 \rbrace$, $\ldots$, $\lbrace p_n \rbrace S_n \lbrace q_n \rbrace$, sin importar el contenido de los subprogramas $S_i$ (noción de **caja negra**).
- Por ejemplo, dado el programa $S :: S_1; S_2$, si se cumplen las fórmulas $\lbrace p \rbrace S_1 \lbrace r \rbrace$ y $\lbrace r \rbrace S_2 \lbrace q \rbrace$, entonces también se cumple la fórmula $\lbrace p \rbrace S_1; S_2 \lbrace q \rbrace$, **independientemente del contenido de $S_1$ y $S_2$**.
- Si en vez de $S_2$ usamos un subprograma $S_3$ que también satisface $\lbrace r \rbrace S_3 \lbrace q \rbrace$, entonces también se cumple la fórmula $\lbrace p \rbrace S_1; S_3 \lbrace q \rbrace$, lo que implica que $S_2$ y $S_3$ son **intercambiables** (son funcionalmente equivalentes respecto de la tupla $(r, q)$).

### Pérdida de la composicionalidad en los programas concurrentes

- En los programas concurrentes, la composicionalidad se pierde porque el orden de ejecución de los subprogramas no es fijo, sino que varía en cada ejecución. Por lo tanto, el resultado de ejecutar un subprograma puede depender del orden de ejecución de los subprogramas, lo que hace que no se puedan intercambiar subprogramas sin afectar el resultado final.
- Por ejemplo, si $\lbrace x = 0 \rbrace S_1 :: x := x + 2 \lbrace x = 2 \rbrace$ y $\lbrace x = 0 \rbrace S_2 :: z := x \lbrace z = 0 \rbrace$, y se ejecutan de forma concurrente, entonces no siempre se cumple que $\lbrace x = 0 \land x = 0 \rbrace [S_1 \parallel S_2] \lbrace x = 2 \land z = 0 \rbrace$, porque si en el programa $S_1 \parallel S_2$ se ejecuta primero $S_1$ y luego $S_2$, al final se cumple que $z = 2$ en vez de $z = 0$.
  - Lo que SÍ vale es $\lbrace x = 0 \land x = 0 \rbrace [S_1 \parallel S_2] \lbrace x = 2 \land (z = 0 \lor z = 2) \rbrace$
  - Además, cambiar $S_1$ por un proceso equivalente $S_3 :: x := x + 1; x := x + 1$ no vale porque si $S_2$ se ejecuta entre medio de las dos asignaciones de $S_3$, entonces al final se cumple que $z = 1$ en vez de $z = 0$ o $z = 2$. Así, **en la concurrencia dos procesos funcionalmente equivalentes NO son intercambiables**.
  - Se pierde la noción de caja negra.

### Especificaciones

- La especificación de un programa para calcular el factorial: $\lbrace x > 0 \rbrace S_{fac} \lbrace y = x! \rbrace$ no es correcta, porque si bien el programa $S :: x := 1; y := 1$ satisface $(x > 0, y = x!)$, no es el programa pedido. Por ejemplo, si al empezar $x = 5$, entonces al final debe ser $y = 5! = 120$ pero se tiene $y = 1$.
- El problema central es que las variables de la precondición pueden ser modificadas a lo largo del programa, efectivamente rompiendo la conexión entre la precondición y la postcondición. Para solucionar esto se introduce el concepto de **variable lógica**.
- Una variable lógica es una variable que aparece en la precondición pero no en el programa, es decir, no es modificada por el programa. Se usan para congelar valores.
- En el ejemplo dado, haríamos $(x = X \land X > 0, y = X!)$ con $X$ la variable lógica.
- No es posible agregar a la especificación que la variable común $x$ no se modifique nunca, ya que la lógica de predicados no lo permite. Una lógica que sí lo permite es la lógica temporal.

### Sensatez, completitud y automatización de la verificación

- La **sensatez** es la propiedad obligatoria de que si una fórmula $\lbrace p \rbrace S \lbrace q \rbrace$ se cumple sintácticamente (con axiomas y reglas) entonces también se cumple semánticamente (considerando estados y computaciones).
- La **completitud** es la propiedad deseable de que si una fórmula $\lbrace p \rbrace S \lbrace q \rbrace$ se cumple semánticamente entonces se puede probar sintácticamente.
  - Su cumplimiento o no depende de la expresividad del lenguaje de especificación.
- La **automatización** no es posible porque la verificación de programas es indecidible en general y por lo tanto no automatizable. Sin embargo, existen muchas herramientas que asisten interactivamente al programador en la verificación de programas. En particular, si los programas son de estados finitos, existen sistemas de verificación automática denominados sistemas de model checking, que usan la lógica temporal y no son sintácticamente orientados como la Lógica de Hoare.
  - Herramientas de verificación axiomática: Dafny, COQ, Isabelle.
  - Herramientas de model checking: EMC, CAESAR, SMV, SPIN.
  - Herramientas de síntesis de programas: búsqueda estocástica, IA.

---

## Correctitud parcial vs total

### Parcial

- La **correctitud parcial** de un programa $S$ con respecto a una especificación $(p, q)$, denotada $\lbrace p \rbrace S \lbrace q \rbrace$, significa que si $S$ se ejecuta a partir de un estado $\sigma$ que satisface $p$, entonces si $S$ termina, lo hace en un estado $\sigma'$ que satisface $q$. No se garantiza que $S$ termine.
- Se puede visualizar vía una tabla de verdad donde:
  - $p:$ el estado inicial satisface $p$.
  - $r:$ $S$ termina.
  - $q:$ el estado final satisface $q$.

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

- Se puede ver que el único caso donde la correctitud parcial no se cumple es cuando el programa se ejecuta a partir de un estado que satisface $p$, el programa termina, pero lo hace en un estado que no satisface $q$.

### Total

- La **correctitud total** de un programa $S$ con respecto a una especificación $(p, q)$, denotada $\langle p \rangle S \langle q \rangle$, significa que si $S$ se ejecuta a partir de un estado $\sigma$ que satisface $p$, entonces $S$ termina en un estado $\sigma'$ que satisface $q$. Se garantiza que $S$ termine.
- Se puede visualizar vía una tabla de verdad donde:
  - $p:$ el estado inicial satisface $p$.
  - $r:$ $S$ termina.
  - $q:$ el estado final satisface $q$.

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

- Se puede ver que hay 2 casos donde la correctitud total no se cumple:
  - Cuando el programa se ejecuta a partir de un estado que satisface $p$, pero el programa no termina, por lo cual no importa si la postcondición se cumple o no.
  - Cuando el programa se ejecuta a partir de un estado que satisface $p$, el programa termina, pero lo hace en un estado que no satisface $q$.

---

## Sensatez y completitud de $H$ y $H*$

### Sensatez de $H$

No puede pasar que **SÍ se pueda demostrar** en $H$, por ejemplo, $\lbrace x = 0 \rbrace x := x + 1 \lbrace x = 2 \rbrace$, porque ocurre que la precondición es verdadera, pero luego de ejecutar el programa no se cumple la postcondición.

### Completitud de $H$

No puede pasar que **NO se pueda demostrar** en $H$, por ejemplo, $\lbrace x = 0 \rbrace y := x \lbrace y = 0 \rbrace$, porque ocurre que la precondición es verdadera y luego de ejecutar el programa se cumple la postcondición, por lo tanto la terna es válida.

### Sensatez de $H*$

No puede pasar que **SÍ se pueda demostrar** en $H*$, por ejemplo, $\langle x = 0 \rangle \text{ while x = 0 do } skip \text{ od} \langle true \rangle$, porque ocurre que la precondición es verdadera, pero el programa no termina.

### Completitud de $H*$

No puede pasar que **NO se pueda demostrar** en $H*$, por ejemplo, $\langle x = 0 \rangle \text{ while x < 10 do } x := x + 1 \text{ od} \langle x = 10 \rangle$,

### Simbología de la sensatez y completitud

- $\vdash_H \lbrace p \rbrace S \lbrace q \rbrace$ expresa que en el sistema $H$ se puede demostrar la fórmula $\lbrace p \rbrace S \lbrace q \rbrace$.
- $\models \lbrace p \rbrace S \lbrace q \rbrace$ expresa que la fórmula $\lbrace p \rbrace S \lbrace q \rbrace$ se cumple **semánticamente**.
- $\vdash_{H*} \langle p \rangle S \langle q \rangle$ expresa que en el sistema $H*$ se puede demostrar la fórmula $\langle p \rangle S \langle q \rangle$.
- $\models \langle p \rangle S \langle q \rangle$ expresa que la fórmula $\langle p \rangle S \langle q \rangle$ se cumple **semánticamente**.
- Se prueba que:
  - Si $\vdash_H \lbrace p \rbrace S \lbrace q \rbrace$ entonces $\models \lbrace p \rbrace S \lbrace q \rbrace$ (**sensatez** de $H$).
  - Si $\models \lbrace p \rbrace S \lbrace q \rbrace$ entonces $\vdash_H \lbrace p \rbrace S \lbrace q \rbrace$ (**completitud** de $H$).
  - Si $\vdash_{H*} \langle p \rangle S \langle q \rangle$ entonces $\models \langle p \rangle S \langle q \rangle$ (**sensatez** de $H*$).
  - Si $\models \langle p \rangle S \langle q \rangle$ entonces $\vdash_{H*} \langle p \rangle S \langle q \rangle$ (**completitud** de $H*$).
- En términos simples:
  - Las fórmulas que demuestran los sistemas $H$ y $H*$ son verdaderas → **Sensatez**.
  - Todas las fórmulas que son verdaderas se pueden demostrar en los sistemas $H$ y $H*$ → **Completitud**.

## Inducción matemática

- Sea $P$ una propie dad que se quiere probar en $\mathbb{N}$.
- Se compone de 3 pasos fundamentales: base inductiva, hipótesis inductiva y paso inductivo.
- **Base inductiva**: Si se cumple que $P(0)$ es verdadera (donde $0$ es el elemento mínimo de $\mathbb{N}$)
- **Hipótesis inductiva**: Supongamos que $P(k)$ es verdadera para algún $k \in \mathbb{N}$.
- **Paso inductivo**: Y además que $\forall k \in \mathbb{N}, P(k) \rightarrow P(k + 1)$, entonces se concluye que para todo $n = 0, 1, 2, \ldots$, $P(n)$ es verdadera.
- Ejemplo de demostración de la sumatoria de $n$ números naturales usando inducción matemática:
  - $\sum_{i = 0}^n i = \frac{n(n + 1)}{2}$
  - **Base inductiva**: $P(0) : \sum_{i = 0}^0 i = \frac{0(0 + 1)}{2}$, es decir, $0 = 0$, lo cual es verdadero.
  - **Hipótesis inductiva**: Supongamos que $P(k) : \sum_{i = 0}^k i = \frac{k(k + 1)}{2}$ es verdadera para algún $k \in \mathbb{N}$.
  - **Paso inductivo**: Entonces, $\sum_{i = 0}^{k + 1} i = \sum_{i = 0}^k i + (k + 1)$. Por hipótesis inductiva, esto es igual a $\frac{k(k + 1)}{2} + (k + 1)$. Factorizando, se obtiene $\frac{k(k + 1) + 2(k + 1)}{2} = \frac{(k + 1)(k + 2)}{2}$, lo cual es igual a $\frac{(k + 1)((k + 1) + 1)}{2}$, y por lo tanto se cumple que $\forall k \in \mathbb{N}, P(k) \rightarrow P(k + 1)$.

## Inducción estructural

- Es más general que la inducción matemática.
- Se usa para definir conjuntos y demostrar sus propiedades.
- Se aplica a cualquier dominio (los naturales, expresiones aritméticas, árboles, programas, etc).
- Puede haber varias bases inductivas y varios pasos inductivos.
- Ejemplo:
  - Definir por I.E las expresiones aritméticas con símbolos del conjunto $\lbrace 0, 1, x, +, \cdot, (, ) \rbrace$
  - **Bases inductivas**: $0$, $1$ y $x$ son expresiones aritméticas.
  - **Pasos inductivos**: si $e$ y $f$ son expresiones aritméticas, entonces $(e + f)$ y $(e \cdot f)$ también lo son.
  - Probar que $C(e) = 1 + O(e)$, donde $C$ es la cantidad de $0$, $1$ y $x$, y $O$ es la cantidad de operadores $+$ y $\cdot$.
  - **Bases inductivas**:
    - $C(0) = 1 + O(0)$
    - $C(1) = 1 + O(1)$
    - $C(x) = 1 + O(x)$
  - **Paso inductivo para el operador $+$**:
    - Supongamos que $C(e) = 1 + O(e)$ y $C(f) = 1 + O(f)$.
    - Entonces, $C(e + f) = C(e) + C(f) = (1 + O(e)) + (1 + O(f)) (hipótesis)
    - Como $O(e + f) = O(e) + 1 + O(f)$, entonces $C(e + f) = 1 + O(e + f)$.

---

## Semántica del lenguaje de programación

### Conceptos básicos

- Para probar las propiedades de sensatez y completitud de $H$ y $H*$, primero hay que definir formalmente la semántica del lenguaje de programación.
- Dados un programa $S$ y un estado inicial $\sigma$, a dicha instancia o configuración inicial $(S, \sigma)$ se le asocia una computación $\pi(S, \sigma)$ que es la secuencia de instancias de la ejecución de $S$ a partir de $\sigma$.
  - Por ejemplo: $(x := 0; y := 1; z := 2, \sigma) \rightarrow (y := 1; z := 2, \sigma[x | 0]) \rightarrow (z := 2, \sigma[x | 0][y | 1]) \rightarrow (E, \sigma[x | 0][ y | 1][z | 2])$.
- $val(\pi(S, \sigma))$ es el estado final de la computación $\pi(S, \sigma)$. Si $\pi(S, \sigma)$ es infinita, entonces $val(\pi(S, \sigma)) = \perp$ (no se detiene).
  - Ejemplo 1: $val(\pi(\text{while true do skip od}, \sigma)) = \perp$.
  - Ejemplo 2: $val(\pi(x := 10; \text{while x > 0 do } x := x - 1 \text{ od}, \sigma)) = \sigma[x | 0]$.

### Definición por inducción estructural

- El lenguaje de programación se define por inducción estructural mediante una relación $\rightarrow$:
- $(skip, \sigma) \rightarrow (E, \sigma)$
  - El $skip$ se consume en un paso (es atómico) y no modifica el estado inicial. $E$ es la continuación sintáctica vacía.
- $(x := e, \sigma) \rightarrow (E, \sigma[x | \sigma(e)])$
  - La asignación $x := e$ es atómica y el estado final es como el inicial salvo que el valor de $x$ es el de la expresión $e$ según $\sigma$.
- Para toda instrucción $T$, si $(S, \sigma) \rightarrow (S', \sigma')$ entonces $(S; T, \sigma) \rightarrow (S'; T, \sigma')$
  - La secuencia $S; T$ se ejecuta de izquierda a derecha. Consumido $S$, si no diverge (si no loopea), se ejecuta $T$.
- $(\text{if } B \text{ then } S_1 \text{ else } S_2 \text{ fi}, \sigma)\rightarrow (S_1, \sigma)$ si se cumple $\sigma(B) = verdadero$
- $(\text{if } B \text{ then } S_1 \text{ else } S_2 \text{ fi}, \sigma)\rightarrow (S_2, \sigma)$ si se cumple $\sigma(B) = falso$
  - La evaluación de la expresión $B$ es atómica y no modifica el estado inicial. Su evaluación establece si se ejecuta $S_1$ o $S_2$.
- $(\text{while } B \text{ do } S \text{ od}, \sigma) \rightarrow (S; \text{while } B \text{ do } S \text{ od}, \sigma)$ si se cumple $\sigma(B) = verdadero$
- $(\text{while } B \text{ do } S \text{ od}, \sigma) \rightarrow (E, \sigma)$ si se cumple $\sigma(B) = falso$
  - La evaluación de la expresión $B$ es atómica y no modifica el estado inicial. Su evaluación establece si se ejecuta el cuerpo $S$ o si se termina el bucle.

### Definición por extensión de la semántica de las instrucciones

- De la definición por comprensión o inductiva de las instrucciones se puede derivar su definición por extensión.
- Por ejemplo, en la secuencia, una computación $\pi(S_1; S_2, \sigma)$ tiene tres formas posibles:
  - Una computación **infinita** $(S_1; S_2, \sigma_0) \rightarrow (T_1; S_2, \sigma_1) \rightarrow (T_2; S_2, \sigma_2) \rightarrow \ldots$ cuando $S_1$ diverge a partir de $\sigma_0$.
  - Una computación **infinita** $(S_1; S_2, \sigma_0) \rightarrow \ldots \rightarrow (S_2, \sigma_1) \rightarrow (T_1, \sigma_2) \rightarrow (T_2, \sigma_3) \rightarrow \ldots$ cuando $S_1$ termina a partir de $\sigma_0$ pero $S_2$ diverge a partir de $\sigma_1$.
  - Una computación **finita** $(S_1; S_2, \sigma_0) \rightarrow \ldots \rightarrow (S_2, \sigma_1) \rightarrow \ldots \rightarrow (E, \sigma_2)$ cuando $S_1$ termina a partir de $\sigma_0$ y $S_2$ termina a partir de $\sigma_1$.
- De forma similar se pueden obtener las formas de las computaciones de los otros tipos de instrucciones.

---

## Prueba de la sensatez del método $H$

- Se cumple, para todo programa $S$ y toda especificación $(p, q)$ que $\vdash_H \lbrace p \rbrace S \lbrace q \rbrace \rightarrow \models \lbrace p \rbrace S \lbrace q \rbrace$.
- Se prueba por inducción matemática fuerte, considerando la longitud de la prueba (1 o más pasos):
  - Base inductiva: los axiomas son verdaderos (pruebas de tamaño 1).
  - Paso inductivo: las reglas son sensatas, es decir, preservan la verdad de las premisas (pruebas de tamaño $\geq 2$)
- Ejemplo 1: Prueba de que el axioma $skip$ es verdadero.
  - Dado $\vdash \lbrace p \rbrace skip \lbrace p \rbrace$, se quiere probar $\models \lbrace p \rbrace skip \lbrace p \rbrace$.
  - Sea $\vdash \lbrace p \rbrace skip \lbrace p \rbrace$.
  - Sea $\sigma \models p$.
  - La semántica del $skip$ es $(skip, \sigma) \rightarrow (E, \sigma)$.
  - Así, luego de un $skip$ queda $\sigma \models p$.
  - Por lo tanto, $\models \lbrace p \rbrace skip \lbrace p \rbrace$.
- Ejemplo 2: Prueba de que la regla SEC es sensata (preserva la verdad de las premisas)
  - Dado $\vdash \lbrace p \rbrace S_1; S_2 \lbrace q \rbrace$ hay que probar $\models \lbrace p \rbrace S_1; S_2 \lbrace q \rbrace$.
  - Sea $\vdash \lbrace p \rbrace S_1; S_2 \lbrace q \rbrace$.
  - Se cumple $\vdash \lbrace p \rbrace S_1 \lbrace r \rbrace$ y $\vdash \lbrace r \rbrace S_2 \lbrace q \rbrace$ para algún $r$.
  - Las pruebas $\vdash \lbrace p \rbrace S_1 \lbrace r \rbrace$ y $\vdash \lbrace r \rbrace S_2 \lbrace q \rbrace$ son más cortas que la prueba $\vdash \lbrace p \rbrace S_1; S_2 \lbrace q \rbrace$, por lo tanto se puede aplicar inducción.
  - Por hipótesis inductiva: $\models \lbrace p \rbrace S_1 \lbrace r \rbrace$ y $\models \lbrace r \rbrace S_2 \lbrace q \rbrace$.
  - Sea $\sigma_1 \models p$.
  - La semántica de la secuencia es $(S_1; S_2, \sigma_1) \rightarrow \ldots \rightarrow (S_2, \sigma_2) \rightarrow \ldots \rightarrow (E, \sigma_3)$.
  - Así, como $\models \lbrace p \rbrace S_1 \lbrace r \rbrace$ y $\models \lbrace r \rbrace S_2 \lbrace q \rbrace$, entonces luego de $S_1; S_2$ queda $\sigma_3 \models q$.
  - Por lo tanto $\models \lbrace p \rbrace S_1; S_2 \lbrace q \rbrace$.

---

## Prueba de la sensatez del método $H*$

- Solo hay que probar que la regla REP\* es sensata.
- $\vdash_{H*} \langle p \rangle \text{ while B do } S \text{ od} \langle p \land \lnot B \rangle \rightarrow \models \langle p \rangle \text{ while B do } S \text{ od} \langle p \land \lnot B \rangle$.
- Sea $\vdash_{H*} \langle p \rangle \text{ while B do } S \text{ od} \langle p \land \lnot B \rangle$.
- Se cumplen dos cosas:
  - $\vdash \langle p \land B \rangle S \langle p \rangle$
  - $\vdash \langle p \land B \land t = Z \rangle S \langle t < Z \rangle, p \rightarrow t \geq 0$
- Las pruebas $\vdash \langle p \land B \rangle S \langle p \rangle$ y $\vdash \langle p \land B \land t = Z \rangle S \langle t < Z \rangle, p \rightarrow t \geq 0$ son más cortas que la prueba $\vdash_{H*} \langle p \rangle \text{ while B do } S \text{ od} \langle p \land \lnot B \rangle$, por lo tanto se puede aplicar inducción.
- Por hipótesis inductiva: $\models \langle p \land B \rangle S \langle p \rangle$ y $\models \langle p \land B \land t = Z \rangle S \langle t < Z \rangle, p \rightarrow t \geq 0$.
- Sea $\sigma_0 \models p$. Hay que probar que el while termina en un estado $\sigma_k \models \langle p \land \lnot B \rangle$.
- Supongamos que el while loopea a partir de $\sigma_0$.
- Así, se tiene la computación infinita $(\text{while B do } S \text{ od}, \sigma_0) \rightarrow (\text{while B do } S \text{ od}, \sigma_1) \rightarrow  (\text{while B do } S \text{ od}, \sigma_2) \rightarrow \ldots$ y por hipótesis inductiva, siempre vale $p, t \geq 0$ y $t$ se decrementa en cada iteración.
- Pero esto no puede pasar, porque si no habría una cadena descendente infinita de números naturales.
- Por lo tanto el while termina y lo hace en algún estado $\sigma_k \models \langle p \land \lnot B \rangle$
