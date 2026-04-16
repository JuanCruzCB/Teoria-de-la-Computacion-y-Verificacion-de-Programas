<h1 align="center">Trabajo Práctico 2</h1>

## 1. Probar que el lenguaje $L_U = \lbrace (\langle M \rangle, w) \mid M \text{ acepta } w \rbrace$ pertenece a la clase $RE$. Comentario: probarlo construyendo una MT.

Para probar que el lenguaje $L_U$ descripto pertenece a la clase $RE$, se debe construir una MT que lo acepte pero no necesariamente se detenga siempre para las cadenas que no son parte del lenguaje. Sea la MT construida $T$:

1. $T$ recibe una cadena de la forma $(\langle M \rangle, w)$, donde $M$ es una MT y $w$ es una cadena.
2. Si $M$ no es una MT válida, $T$ rechaza.
3. Si $M$ es una MT válida, $T$ simula la ejecución de $M$ sobre la cadena $w$.
4. Si durante la simulación $M$ **acepta** $w$, entonces $T$ acepta la cadena de entrada $(\langle M \rangle, w)$.
5. Si durante la simulación $M$ **rechaza** o **loopea** $w$, entonces $T$ no acepta la cadena de entrada $(\langle M \rangle, w)$, ya sea rechazando o loopeando.

De esta forma se cumple que si $(\langle M \rangle, w) \in L_U$, entonces $M$ acepta, y si $(\langle M \rangle, w) \notin L_U$, entonces $M$ no acepta, ya sea rechazando o loopeando. Por lo tanto, $L_U \in RE$.

## 2. Responder breve y claramente cada uno de los siguientes incisos (en todos los casos, las MT mencionadas tienen una sola cinta):

### a. Probar que se puede decidir si una MT $M$, a partir de la cadena vacía $\lambda$, escribe alguna vez un símbolo no blanco. Ayuda: ¿Cuántos pasos puede hacer $M$ antes de entrar en un loop?

...

### b. Probar que se puede decidir si una MT $M$ que sólo se mueve a la derecha, a partir de una cadena $w$, para, Ayuda: ¿Cuántos pasos puede hacer $M$ antes de entrar en un loop?

...

### c. Probar que se puede decidir si dada una MT $M$, existe una cadena $w$ a partir de la cual $M$ para en a lo sumo 10 pasos. Ayuda: ¿Hasta qué tamaño de cadenas hay que chequear?

...

### d. ¿Se puede decidir si dada una MT $M$, existe una cadena $w$ de a lo sumo 10 símbolos a partir de la cual $M$ para? Justificar la respuesta.

...

## 3. Sea $M_1$ una MT que genera un lenguaje recursivo $L$ sin repetir cadenas y siguiendo el orden canónico. Probar que existe una MT $M_2$ que decide $L$. Ayuda: cuidado con el caso en que $L$ sea finito.

...

## 4. Considerando la reducción de $HP$ a $L_U$ descripta en clase, responder:

### a. Explicar por qué la función identidad, es decir la función que a toda cadena le asigna la misma cadena, no es una reducción de $HP$ a $L_U$.

La función identidad $f(x) = x$ no es una reducción de $HP$ a $L_U$ porque no cumple con la propiedad fundamental de las reducciones que es que para toda cadena $w$, si $w \in HP$ entonces $f(w) \in L_U$, y si $w \notin HP$ entonces $f(w) \notin L_U$. En particular, con la función identidad pasa lo siguiente:

1. Si $(\langle M \rangle, w) \notin HP$, entonces la máquina no se detiene a partir de $w$, y luego de aplicarle la función identidad se obtiene exactamente el mismo par tal que $(\langle M \rangle, w) \notin L_U$ porque $M$ no acepta $w$ (ya que no se detiene, y no detenerse implica no aceptar). Por lo tanto hasta ahora todo bien.
2. Si $(\langle M \rangle, w) \in HP$, entonces la máquina se detiene a partir de $w$, pero esto no necesariamente implica que acepta esa cadena, ya que se puede haber detenido en el estado $q_R$, lo cual viola la definición de $L_U$. Por ende $f(\langle M \rangle, w)$ no siempre pertenece a $L_U$ y por lo tanto se rompe la reducción.

### b. Explicar por qué las MT $M_2$ generadas en los pares de salida $(\langle M_2 \rangle, w)$, o bien paran aceptando, o bien loopean.

Lo que hace la función $f(\langle M_1 \rangle, w) = (\langle M_2 \rangle, w)$ en la reducción descripta en clase es cambiar todos los estados $q_R$ de la máquina $M_1$ por estados $q_A$. Por lo tanto transforma la máquina original en una máquina que si antes rechazaba, ahora acepta. Sin embargo, esto no afecta para nada al caso en que la máquina loopeaba con la cadena $w$, ya que el cambio de estados no afecta a los loopeos. Por ende las máquinas $M_2$ generadas en los pares de salida $(\langle M_2 \rangle, w)$, o bien paran aceptando (si $M_1$ se detenía ya sea aceptando o rechazando), o bien loopean (si $M_1$ loopeaba).

El motivo de esta transformación es para garantizar que la propiedad fundamental de la reducción se cumpla:

1. Si $(\langle M_1 \rangle, w) \in HP$, entonces $M_1$ se detiene a partir de $w$, lo cual implica que $M_2$ se detiene en $q_A$ a partir de $w$, y por lo tanto $f(\langle M_1 \rangle, w) = (\langle M_2 \rangle, w) \in L_U$.
2. Si $(\langle M_1 \rangle, w) \notin HP$, entonces $M_1$ no se detiene a partir de $w$, lo cual implica que $M_2$ tampoco se detiene a partir de $w$, y por lo tanto $f(\langle M_1 \rangle, w) = (\langle M_2 \rangle, w) \notin L_U$.

### c. Explicar por qué la función utilizada para reducir $HP$ a $L_U$ también sirve para reducir $HP^C$ a $L_U^C$.

$HP^C = \lbrace (\langle M \rangle, w) \mid M \text{ no se detiene a partir de } w \rbrace$

$L_U^C = \lbrace (\langle M \rangle, w) \mid M \text{ no acepta } w \rbrace$

Probando que la función utilizada para reducir $HP$ a $L_U$ también sirve para reducir $HP^C$ a $L_U^C$:

1. Si $(\langle M_1 \rangle, w) \in HP^C$, entonces $M_1$ no se detiene a partir de $w$, lo cual implica que $M_2$ tampoco se detiene a partir de $w$, y por lo tanto $f(\langle M_1 \rangle, w) = (\langle M_2 \rangle, w) \in L_U^C$.
2. Si $(\langle M_1 \rangle, w) \notin HP^C$, entonces $M_1$ se detiene a partir de $w$, lo cual implica que $M_2$ se detiene en $q_A$ a partir de $w$, y por lo tanto $f(\langle M_1 \rangle, w) = (\langle M_2 \rangle, w) \notin L_U^C$.

La razón fundamental de por qué la función también sirve acá es porque quedarse loopeando implica no aceptar, y por lo tanto esos casos están dentro de $L_U^C$.

### d. Explicar por qué la función utilizada para reducir $HP$ a $L_U$ no sirve para reducir $L_U$ a $HP$.

Analizando los dos casos:

1. Si $(\langle M_1 \rangle, w) \in L_U$, entonces $M_1$ acepta $w$, lo cual implica que $M_2$ se detiene en $q_A$ a partir de $w$, y por lo tanto $f(\langle M_1 \rangle, w) = (\langle M_2 \rangle, w) \in HP$.
2. Si $(\langle M_1 \rangle, w) \notin L_U$, entonces $M_1$ no acepta $w$, pero esto no necesariamente implica que $M_1$ loopea a partir de $w$, ya que se puede haber detenido en el estado $q_R$. En este caso, $M_2$ se detiene en $q_A$ a partir de $w$, y por lo tanto $f(\langle M_1 \rangle, w) = (\langle M_2 \rangle, w) \in HP$, lo cual rompe la reducción.

### e. Explicar por qué la siguiente MT $M_f$ no computa una reducción de $HP$ a $L_U$: dada una cadena válida $(\langle M \rangle, w)$, $M_f$ ejecuta $M$ sobre $w$, si $M$ acepta entonces genera la salida $(\langle M \rangle, w)$, y si $M$ rechaza entonces genera la cadena $1$.

Nuevamente analizando los dos casos:

1. Si $(\langle M \rangle, w) \in HP$, entonces $M$ se detiene a partir de $w$. $M_f$ ejecuta $M$ sobre $w$, y si $M$ acepta entonces genera la salida $(\langle M \rangle, w)$, pero si rechaza entonces genera la cadena $1$. Como $HP$ posee máquinas que se detienen tanto aceptando como rechazando, entonces $M_f$ puede fácilmente dar como resultado la cadena $1$ para una máquina que se detiene rechazando, y como $1 \notin L_U$ se rompe la reducción.
2. No es necesario analizar el caso en que $(\langle M \rangle, w) \notin HP$ porque ya se mostró que la función no es una reducción válida.

## 5. Sabiendo que $L_U \in RE$ y $L_U^C \in \text{CO-RE}$:

### a. Probamos en clase que existe una reducción de $L_U$ a $L_{\Sigma^*}$. En base a esto, ¿qué se puede afirmar con respecto a la ubicación de $L_{\Sigma^*}$ en la jerarquía de la computabilidad?

1. Se sabe que $L_U \in (RE - R)$.
2. Se sabe por propiedad que si dados dos lenguajes $L_1$ y $L_2$ tales que $L_1 \leq L_2$ y $L_1 \notin R$, entonces $L_2 \notin R$.
3. Como se sabe que $L_U \notin R$ y se ha probado que existe una reducción de $L_U$ a $L_{\Sigma^*}$, entonces se puede afirmar que $L_{\Sigma^*} \notin R$.
4. No se puede afirmar nada más, como por ejemplo si $L_{\Sigma^*}$ está o no en $RE$.

### b. Se prueba que existe una reducción de $L_U^C$ a $L_{\emptyset}$. En base a esto, ¿qué se puede afirmar con respecto a la ubicación de $L_{\emptyset}$ en la jerarquía de la computabilidad?

1. Se sabe que $L_U^C \in (\text{CO-RE} - R)$ y además que $L_U^C \notin RE$.
2. Se sabe por propiedad que si dados dos lenguajes $L_1$ y $L_2$ tales que $L_1 \leq L_2$ y $L_1 \notin RE$, entonces $L_2 \notin RE$.
3. Como se sabe que $L_U^C \notin RE$ y se ha probado que existe una reducción de $L_U^C$ a $L_{\emptyset}$, entonces se puede afirmar que $L_{\emptyset} \notin RE$.

## 6. Sea el lenguaje $D_{HP} = \lbrace w_i \mid M_i \text{ para a partir de } w_i \rbrace$ (considerar el orden canónico}. Encontrar una reducción de $D_{HP}$ a $HP$. Comentario: hay que definir la función de reducción y probar su total computabilidad y correctitud.

$D_{HP} = \lbrace w_i \mid M_i \text{ para a partir de } w_i \rbrace$
$HP = \lbrace (\langle M \rangle, w) \mid M \text{ se detiene a partir de } w \rbrace$

Se quiere encontrar una reducción $D_{HP} \leq HP$.

1. Definición de reducción: para toda cadena $w_i \in D_{HP}$, se debe cumplir:
   1. Si $w_i \in D_{HP}$, entonces $f(w_i) \in HP$.
   2. Si $w_i \notin D_{HP}$, entonces $f(w_i) \notin HP$.
2. Se define una MT $M_f$ que computa la función de reducción $f$, simbólicamente $f(w_i) = (\langle M_i \rangle, w_i)$.
3. La función $f$ hace lo siguiente:
   1. Recibe una cadena $w_i$.
   2. Genera cadenas $v_1, v_2, \ldots, v_j$ en el orden canónico hasta que $v_j = w_i$. De esta forma hallamos el índice $i$ de la cadena original, que no lo sabíamos de antemano.
   3. Genera MTs $M_1, M_2, \ldots, M_i$ en el orden canónico hasta llegar a $M_i$.
   4. Devuelve la cadena $(\langle M_i \rangle, w_i)$.
4. Total computabilidad: la función $f$ es total computable porque para toda cadena $w_i$ se puede hallar su índice $i$ generando cadenas en el orden canónico, y luego se puede generar la MT $M_i$ también en el orden canónico. Por lo tanto, para toda cadena de entrada $w_i$, la función $f$ devuelve una salida válida en tiempo finito, ya que sea cual sea $w_i$, se sabe que está en el orden canónico (porque éste contiene TODAS las cadenas), y por lo tanto se llegará a ella en tiempo finito.
5. Correctitud:
   1. Si $w_i \in D_{HP}$, entonces $M_i$ se detiene a partir de $w_i$, lo cual implica que $(\langle M_i \rangle, w_i) \in HP$, y por lo tanto $f(w_i) \in HP$.
   2. Si $w_i \notin D_{HP}$, entonces $M_i$ no se detiene a partir de $w_i$, lo cual implica que $(\langle M_i \rangle, w_i) \notin HP$, y por lo tanto $f(w_i) \notin HP$.

**Por lo tanto, $D_{HP} \leq HP$**.

## 7. Sean $TAUT$ y $NOSAT$ los lenguajes de las fórmulas booleanas sin cuantificadores tautológicas (satisfactibles por todas las asignaciones de valores de verdad) e insatisfactibles (ninguna asignación de valores de verdad las satisface), respectivamente. Encontrar una reducción de $TAUT$ a $NOSAT$. Comentario: hay que definir la función de reducción y probar su total computabilidad y correctitud.

## 8. Se prueba que existe una reducción de $L_U^C$ a $L_{\Sigma^*}$ (y así, como $L_U^C \notin RE$, entonces se cumple que $L_{\Sigma^*} \notin RE$). La reducción es la siguiente. Para toda $w: f(( \langle M_1 \rangle, w)) = \langle M_2 \rangle$, tal que $M_2$, a partir de su entrada $v$, ejecuta $|v|$ pasos de $M_1$ a partir de $w$, y acepta sii $M_1$ no acepta. Probar que la función definida es efectivamente una reducción de $L_U^C$ a $L_{\Sigma^*}$ (es total computable y correcta).
