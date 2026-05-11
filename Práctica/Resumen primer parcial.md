<h1 align="center">Resumen primer parcial<h1>

## Máquinas de Turing

### Tipos de problemas con MT

- Problema de **búsqueda**: La MT devuelve una respuesta (cadena, número, etc.) o no devuelve nada (rechazo, estado $q_R$).
- Problema de **decisión**: La MT responde sí (aceptación, estado $q_A$) o no (rechazo, estado $q_R$).

### Máquina de Turing (MT)

- **Cinta** infinita dividida en celdas, cada una con un símbolo de un alfabeto finito.
- **Cabezal** que se mueve un paso a la izquierda o derecha, o se queda en la misma posición, y que puede leer y escribir símbolos en la cinta.
- **Estados** finitos, incluyendo un estado inicial, estados de aceptación y estados de rechazo.
- La MT cambia de estado en cada paso según una función de transición que depende del estado actual y del símbolo que está leyendo el cabezal.
- En un paso una MT puede modificar el símbolo que está leyendo, cambiar de estado y moverse un lugar a la izquierda o a la derecha, o quedarse en la misma posición.
- Al iniciar, la cadena de entrada se delimita por infinitos blancos a ambos lados y el cabezal apunta al primer símbolo de la cadena. El estado inicial siempre es $q_0$.
- **Tesis de Church-Turing**: Todo lo que es computable por un algoritmo es computable por una MT.

### Modelos equivalentes de MT

- Dos MT son equivalentes si aceptan el mismo lenguaje.
- Dos modelos de MT son equivalentes si dada una MT de un modelo se puede construir una MT del otro modelo que sea equivalente a la primera.
- Algunos modelos equivalentes al modelo estándar de MT con una cinta:
  - MT con $k$ cintas.
  - MT con cintas semi-infinitas.
  - MT con 2 cintas pero un solo estado.
  - MT no determinísticas.
- Ejemplos de modelos computacionales equivalentes al modelo de MT:
  - Máquinas RAM.
  - Circuitos booleanos.
  - Cálculo lambda.
  - Funciones recursivas parciales.
  - Gramáticas.
  - Programas Java.
  - etc.
- Todo lo anterior refuerza la Tesis de Church-Turing.

### Otros tipos de MT

#### MT calculadora

- Se usa para problemas de búsqueda.
- Realiza un cálculo, generalmente matemático, y devuelve un resultado.
- Además del estado en el cual termina la máquina, importa qué es lo que deja en la cinta, ya que ese es el resultado del cálculo.

#### MT generadora

- Se trata de una MT que genera, una por una, todas las cadenas de un lenguaje en particular.
- En general la generación se hace en orden canónico (primero las cadenas más cortas, luego las más largas).
- **Teorema**: Existe una MT $M$ que acepta un lenguaje $L$ si y solo si existe una MT generadora $M'$ que genera $L$.
  - Si $M$ acepta $L$, entonces $M'$ genera $L$.
  - Si $M'$ genera $L$, entonces $M$ acepta $L$.

---

## Jerarquía de Computabilidad

### Lenguajes recursivos $(R)$

- Un lenguaje $L$ es **recursivo** $(L \in R)$ si y solo si existe una MT $M$ que lo acepta y siempre se detiene.
  - Si $w \in L$, entonces $M$ a partir de $w$ se detiene en el estado de aceptación $q_A$.
  - Si $w \notin L$, entonces $M$ a partir de $w$ se detiene en el estado de rechazo $q_R$.

### Lenguajes recursivamente enumerables $(RE)$

- Un lenguaje $L$ es **recursivamente enumerable** $(L \in RE)$ si y solo si existe una MT $M$ que lo acepta.
  - Si $w \in L$, entonces $M$ a partir de $w$ se detiene en el estado de aceptación $q_A$.
  - Si $w \notin L$, entonces $M$ a partir de $w$ se detiene en el estado de rechazo $q_R$ o no se detiene.

### Propiedades de la clase $R$

1. **Si $L \in R$ entonces $L^C \in R$, con $L^C = \Sigma^* - L$**. Demostración breve:
   1. Dada una MT $M_L$ que acepta $L$ y siempre se detiene, se construye una MT $M_{L^C}$ que acepta $L^C$ y siempre se detiene.
   2. $M_{L^C}$ es igual a $M_L$ excepto que los estados de aceptación y rechazo se intercambian. Es decir, todas las transiciones que van al estado de aceptación $q_A$ de $M_L$ van al estado de rechazo $q_R$ de $M_{L^C}$, y todas las transiciones que van al estado de rechazo $q_R$ de $M_L$ van al estado de aceptación $q_A$ de $M_{L^C}$.
   3. Así, $L^C \in R$.
2. **Si $L_1 \in R$ y $L_2 \in R$ entonces $L_1 \cap L_2 \in R$**. Demostración breve:
   1. Dadas dos MT $M_1$ y $M_2$ que aceptan $L_1$ y $L_2$ respectivamente y siempre se detienen, se construye una MT $M$ que acepta $L_1 \cap L_2$ y siempre se detiene.
   2. $M$ ejecuta secuencialmente primero $M_1$ y luego $M_2$. Si $M_1$ acepta, entonces $M$ ejecuta $M_2$. Si $M_2$ acepta, entonces $M$ acepta. En cualquier otro caso, $M$ rechaza. Como tanto $M_1$ como $M_2$ siempre se detienen, $M$ también siempre se detiene.
   3. Así, $L_1 \cap L_2 \in R$.

### Propiedades de la clase $RE$

1. **Si $L_1 \in RE$ y $L_2 \in RE$ entonces $L_1 \cup L_2 \in RE$**. Demostración breve:
   1. Dadas dos MT $M_1$ y $M_2$ que aceptan $L_1$ y $L_2$ respectivamente, se construye una MT $M$ que acepta $L_1 \cup L_2$.
   2. $M$ ejecuta simultáneamente (en paralelo) $M_1$ y $M_2$. Si cualquiera de las dos máquinas acepta, entonces $M$ acepta. En cualquier otro caso, $M$ no se detiene.
   3. Así, $L_1 \cup L_2 \in RE$.

### Diagrama de Venn de la jerarquía de computabilidad

![Regiones de la jerarquía de la computabilidad](https://i.imgur.com/9mVb6j5.png)

1. **Conjunto $R$**.
   1. Lenguajes aceptados por MT que siempre paran.
   2. Si $L$ está en $R$, entonces $L^C$ también está en $R$.
2. **Conjunto $RE - R$**.
   1. Lenguajes aceptados por MT que no siempre paran.
   2. Si $L$ está en $RE$, entonces $L^C$ está en $\text{CO-RE}$.
3. **Conjunto $\text{CO-RE} - R$**.
   1. Lenguajes que no son aceptados por ninguna MT, pero sus complementos sí son aceptados por alguna MT.
   2. Si $L$ está en $\text{CO-RE}$, entonces $L^C$ está en $RE$.
4. **Conjunto $\mathcal{L} - (RE \cup \text{CO-RE})$**.
   1. Lenguajes que no son aceptados por ninguna MT, ni tampoco sus complementos son aceptados por alguna MT.
   2. Si $L$ está en $\mathcal{L} - (RE \cup \text{CO-RE})$, entonces $L^C$ también está en $\mathcal{L} - (RE \cup \text{CO-RE})$.

---

## Diagonalización

### El lenguaje $D$

- Se tiene un lenguaje $D \in RE - R$ que se usa para probar que $R \subset RE$.
- Se tiene un lenguaje $D^C \in \text{CO-RE} - R$ que se usa para probar que $RE \subset \mathcal{L}$.
- El proceso es el siguiente:
  - Se prueba de forma constructiva que $D \in RE$.
  - Se prueba de forma no constructiva por diagonalización que $D^C \notin RE$.
  - Finalmente se concluye que $D \notin R$, porque si $D \in R$ entonces $D^C \in R$ cosa que es absurdo porque se sabe que $D^C \notin RE$.

### Detalle de la diagonalización

- Se tiene una tabla donde cada fila corresponde a una MT $M_i$ y cada columna corresponde a una cadena $w_j$.
- En cada celda $(i, j)$ se pone un 1 si $M_i$ acepta $w_j$, y un 0 si $M_i$ rechaza $w_j$ ya sea porque se detiene en el estado de rechazo $q_R$ o porque no se detiene.
- La diagonal de la tabla representa el lenguaje $D = \lbrace w_i \mid M_i \text{ acepta } w_i \rbrace$
- La diagonal de la tabla con los bits invertidos representa el lenguaje $D^C = \lbrace w_i \mid M_i \text{ rechaza } w_i \rbrace$
- Se cumple que $D \in (RE - R)$ y $D^C \in (\text{CO-RE} - R)$.

### MT universal

- Una MTU es una MT capaz de ejecutar otra.
- El esquema más general de una MTU es el siguiente:
  - La MTU recibe como cadena de entrada una tupla $( \langle M \rangle, w)$ donde $M$ es la codificación binaria de una MT y $w$ es una cadena de entrada.
  - La MTU ejecuta a la MT $M$ a partir de la cadena $w$.

### Codificación y enumeración de MT

- Cada MT se puede codificar como una cadena binaria, es decir, cada MT tiene una codificación única $\langle M \rangle$.
- Se puede enumerar todas las MTs como $M_1, M_2, M_3, \ldots$, donde $\langle M_i \rangle$ es la codificación de la MT $M_i$.
- Esta enumeración se hace en el **orden canónico**:
  - De menor a mayor longitud.
  - Con longitudes iguales se sigue el orden alfanumérico.
- Para obtener la MT $M_i$ según el orden canónico se puede usar el siguiente algoritmo:
  1. $n = 0$
  2. Genera la siguiente cadena $w$ según el orden canónico.
  3. Si $w$ no es la codificación válida de una MT (esto se chequea fácilmente de forma sintática) vuelve al paso 2.
  4. Si $n = i$, devuelve $w$, que es el código de la MT $M_i$, y se detiene. Si $n \neq i$, hace $n = n + 1$ y vuelve al paso 2.

### Halting Problem

- El **Halting Problem** $(HP)$ postula: dada una MT $M$ y una cadena de entrada $w$, ¿$M$ se detiene a partir de $w$?
- Formalmente, $HP = \lbrace ( \langle M \rangle, w) \mid M \text{ se detiene a partir de } w \rbrace$
- $HP \in (RE - R)$. Se prueba por diagonalización.

### Formas de burlar al Halting Problem

- Si bien el Halting Problem es indecidible, con ciertas restricciones al problema como tal se vuelve decidible.

#### Detección de loopeo

- Si una MT se mueve en un espacio de celdas limitado, se puede detectar cuándo entra en loop.
- Supongamos que $M$ se mueve en no más de $k$ celdas. ¿Por cuántas configuraciones distintas puede pasar $M$ antes de loopear?
- Una configuración de una MT tiene:
  - Una posición.
  - Un estado.
  - Un contenido.
- Si $M$ tiene $|Q|$ estados y $|\Gamma|$ símbolos, entonces hará a lo sumo $k \cdot |Q| \cdot |\Gamma|^k$ pasos antes de repetir una configuración.
  - $k$ posiciones.
  - $|Q|$ estados.
  - $|\Gamma|^k$ contenidos posibles.
- Por lo tanto, se puede detectar si una MT loopea ejecutándola y llevando la cuenta de sus pasos. Si llega a $k \cdot |Q| \cdot |\Gamma|^k$ pasos sin detenerse, entonces se concluye que $M$ loopea.

#### Detección de aceptación de al menos una cadena

- ¿Cómo detectar si una MT $M$ acepta al menos una cadena?
- Tenemos que tener precaución en cómo construimos la MT $M'$ que chequea si $M$ acepta al menos una cadena. No sirve que $M'$ ejecute $M$ con todas las cadenas posibles en orden canónico, porque si $M$ no se detiene con alguna cadena, entonces $M'$ tampoco se detendrá y nunca dará una respuesta.
- Solución:
  1. $i = 1$
  2. Ejecutar $i$ pasos de $M$ sobre TODAS las cadenas de longitud a lo sumo $i$.
  3. Si $M$ acepta alguna de esas cadenas, entonces $M'$ acepta.
  4. Si no, entonces $i = i + 1$ y se vuelve al paso 2.
- Por ejemplo, si la primer cadena que $M$ acepta es de 80 símbolos y $M$ la acepta en 120 pasos, entonces cuando $M'$ ejecute 120 pasos de $M$ sobre todas las cadenas de a lo sumo 120 símbolos la encontrará y aceptará.

### Computabilidad en relación al tamaño de un lenguaje

- La computabilidad de un lenguaje tiene más que ver con su definición que con su tamaño.
- Por ejemplo, el lenguaje $\Sigma^*$ es el "más grande" posible, y sin embargo es decidible ("fácil"), mientras que $HP$ es un lenguaje mucho más pequeño que $\Sigma^*$, pero no es decidible ("difícil").

---

## Reducciones

### Definición

- Dados dos lenguajes $L_1$ y $L_2$, supongamos que existe una MT $M_f$ que computa una función $f: \Sigma^* \to \Sigma^*$ tal que:
  - A partir de todo $w \in L_1$, $M_f$ devuelve $f(w) \in L_2$.
  - A partir de todo $w \notin L_1$, $M_f$ devuelve $f(w) \notin L_2$.
- Entonces se dice que la función $f$ es una **reducción** de $L_1$ a $L_2$, se denota como $L_1 \leq L_2$, y se dice que $f$ es **total computable** porque se computa sobre todas las cadenas.

### Recordatorio de la equivalencia lógica contrarrecíproca

- $p \rightarrow q$ es equivalente a $\neg q \rightarrow \neg p$.

### Teoremas de las reducciones

1. Si $L_1 \leq L_2$ y $L_2 \in R$, entonces $L_1 \in R$.
   1. También, por contrarrecíproco, si $L_1 \leq L_2$ y $L_1 \notin R$, entonces $L_2 \notin R$.
2. Si $L_1 \leq L_2$ y $L_2 \in RE$, entonces $L_1 \in RE$.
   1. También, por contrarrecíproco, si $L_1 \leq L_2$ y $L_1 \notin RE$, entonces $L_2 \notin RE$.
3. De forma más resumida:
   1. Si $L_1 \leq L_2$ y $L_1$ es difícil $(L_1 \notin R)$ entonces no puede ocurrir que $L_2$ sea fácil $(L_2 \in R)$.
   2. Si $L_1 \leq L_2$ y $L_1$ es muy difícil $(L_1 \notin RE)$ entonces no puede ocurrir que $L_2$ sea fácil o medianamente difícil $(L_2 \in RE)$.
   3. **$L_2$ es tan o más difícil que $L_1$, porque resolviendo $L_2$ se resuelve $L_1$**.
   4. De esta manera, las reducciones permiten hallar lenguajes dentro y fuera de $R$ y $RE$.

### Ejemplo $HP \leq L_U$

- $HP = \lbrace ( \langle M \rangle, w) \mid M \text{ se detiene a partir de } w \rbrace$
- $L_U = \lbrace ( \langle M \rangle, w) \mid M \text{ acepta } w \rbrace$
- De acuerdo al teorema, si $HP \leq L_U$ y $HP \notin R$, entonces $L_U \notin R$.
- Por ende, como se sabe que $HP \notin R$, si se logra probar que $HP \leq L_U$ entonces se concluye que $L_U \notin R$. **Reducción**:
- **Definición**:
  - $f(( \langle M_1 \rangle, w )) = (\langle M_2 \rangle, w)$ con $M_2$ igual a $M_1$ pero con las transiciones hacia el estado $q_R$ cambiadas por transiciones hacia el estado $q_A$.
- **Computabilidad**:
  - Existe una MT $M_f$ que computa la función $f$: copia $(\langle M_1 \rangle, w)$ pero cambiando los estados $q_R$ de $M_1$ por estados $q_A$ en la codificación de $M_2$.
- **Correctitud**:
  - Si $(\langle M_1 \rangle, w) \in HP$, entonces $M_1$ se detiene a partir de $w$. Como las transiciones hacia $q_A$ de $M_1$ se mantienen en $M_2$, entonces $M_2$ acepta $w$. Por lo tanto, $(\langle M_2 \rangle, w) \in L_U$.
  - Si $(\langle M_1 \rangle, w) \notin HP$, entonces $M_1$ no se detiene a partir de $w$. Tenemos dos casos:
    - Si $\langle M_1 \rangle$ no es una codificación válida de MT entonces $\langle M_2 \rangle$ tampoco. Por lo tanto $(\langle M_2 \rangle, w) \notin L_U$.
    - Si $\langle M_1 \rangle$ es una codificación válida de MT, entonces $M_2$ no se detiene a partir de $w$. Por lo tanto, $(\langle M_2 \rangle, w) \notin L_U$.
- Por lo tanto queda demostrado que $HP \leq L_U$ y por lo tanto $L_U \notin R$.

### Propiedades de las reducciones

1. **Reflexividad**: Para todo lenguaje $L$ se cumple $L \leq L$ usando la función de reducción identidad $f(w) = w$.
2. **Transitividad**: Si $L_1 \leq L_2$ y $L_2 \leq L_3$ entonces $L_1 \leq L_3$. Demostración breve:
   1. Si $L_1 \leq L_2$ entonces existe una función de reducción $f$ de $L_1$ a $L_2$.
   2. Si $L_2 \leq L_3$ entonces existe una función de reducción $g$ de $L_2$ a $L_3$.
   3. Se construye una función de reducción $h$ de $L_1$ a $L_3$ tal que $h(w) = g(f(w))$.
   4. Por lo tanto, $L_1 \leq L_3$.
3. **Simetría**: No se cumple. Si $L_1 \leq L_2$ no implica que $L_2 \leq L_1$.
4. **Complemento**: $L_1 \leq L_2$ si y solo si $L_1^C \leq L_2^C$. Se usa exactamente la misma función de reducción $f$ para ambas reducciones.
