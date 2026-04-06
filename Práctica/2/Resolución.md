<h1 align="center">Trabajo Práctico 2</h1>

## 1. Probar que el lenguaje $L_U = \lbrace (\langle M \rangle, w) \mid \text{M acepta w} \rbrace$ pertenece a la clase $RE$. Comentario: probarlo construyendo una MT.

Para probar que el lenguaje $L_U$ descripto pertenece a la clase $RE$, se debe construir una MT que lo acepte pero no necesariamente se detenga siempre para las cadenas que no son parte del lenguaje. Sea la MT construida $M$:

1. $M$ recibe una cadena de la forma $(\langle M' \rangle, w)$, donde $M'$ es una MT y $w$ es una cadena.
2. Si $M'$ no es una MT válida, $M$ rechaza.
3. Si $M'$ es una MT válida, $M$ simula la ejecución de $M'$ sobre la cadena $w$.
4. Si durante la simulación, $M'$ acepta $w$, entonces $M$ acepta la cadena de entrada $(\langle M' \rangle, w)$.
5. Si durante la simulación, $M'$ rechaza $w$, entonces $M$ rechaza la cadena de entrada $(\langle M' \rangle, w)$.
6. Si durante la simulación, $M'$ entra en un loop (es decir, no acepta ni rechaza $w$), entonces $M$ también entra en un loop y no se detiene.

De esta forma se cumple que si $(\langle M' \rangle, w) \in L_U$, entonces $M$ acepta, y si $(\langle M' \rangle, w) \notin L_U$, entonces $M$ no acepta, ya sea rechazando o loopeando. Por lo tanto, $L_U \in RE$.

## 2. Responder breve y claramente cada uno de los siguientes incisos (en todos los casos, las MT mencionadas tienen una sola cinta):

### a. Probar que se puede decidir si una MT $M$, a partir de la cadena vacía $\lambda$, escribe alguna vez un símbolo no blanco. Ayuda: ¿Cuántos pasos puede hacer $M$ antes de entrar en un loop?

Se tiene una MT $M$ que recibe como cadena de entrada $w$ la cadena vacía. Es decir, $w = \lambda$.

Se quiere probar que se puede decidir si $M$ escribe alguna vez un símbolo distinto de blanco en la cinta o si siempre escribe símbolos blancos, lo que implica que loopea.

Se sabe que $Q$, el conjunto de estados de $M$, es **finito**, así como también es finito el alfabeto de la cinta $\Gamma$. Lo importante a notar es que las únicas transiciones para cada estado que podrán ser ejecutadas son aquellas que tengan como símbolo leído $B$, ya que la cadena de entrada es vacía. 

### b. Probar que se puede decidir si una MT $M$ que sólo se mueve a la derecha, a partir de una cadena $w$, para, Ayuda: ¿Cuántos pasos puede hacer $M$ antes de entrar en un loop?

### c. Probar que se puede decidir si dada una MT $M$, existe una cadena $w$ a partir de la cual $M$ para en a lo sumo 10 pasos. Ayuda: ¿Hasta qué tamaño de cadenas hay que chequear?

### d. ¿Se puede decidir si dada una MT $M$, existe una cadena $w$ de a lo sumo 10 símbolos a partir de la cual $M$ para? Justificar la respuesta.

## 3. Sea $M_1$ una MT que genera un lenguaje recursivo $L$ sin repetir cadenas y siguiendo el orden canónico. Probar que existe una MT $M_2$ que decide $L$. Ayuda: cuidado con el caso en que $L$ sea finito.

## 4. Considerando la reducción de $HP$ a $L_U$ descripta en clase, responder:

### a. Explicar por qué la función identidad, es decir la función que a toda cadena le asigna la misma cadena, no es una reducción de $HP$ a $L_U$.

### b. Explicar por qué las MT $M_2$ generadas en los pares de salida $(\langle M_2 \rangle, w)$, o bien paran aceptando, o bien loopean.

### c. Explicar por qué la función utilizada para reducir $HP$ a $L_U$ también sirve para reducir $HP^C$ a $L_U^C$.

### d. Explicar por qué la función utilizada para reducir $HP$ a $L_U$ no sirve para reducir $L_U$ a $HP$.

### e. Explicar por qué la siguiente MT $M_f$ no computa una reducción de $HP$ a $L_U$: dada una cadena válida $(\langle M \rangle, w)$, $M_f$ ejecuta $M$ sobre $w$, si $M$ acepta entonces genera la salida $(\langle M \rangle, w)$, y si $M$ rechaza entonces genera la cadena $1$.

## 5. Sabiendo que $L_U \in RE$ y $L_U^C \in \text{CO-RE}$:

### a. Probamos en clase que existe una reducción de $L_U$ a $L_{\Sigma^*}$. En base a esto, ¿qué se puede afirmar con respecto a la ubicación de $L_{\Sigma^*}$ en la jerarquía de la computabilidad?

### b. Se prueba que existe una reducción de $L_U^C$ a $L_{\emptyset}$. En base a esto, ¿qué se puede afirmar con respecto a la ubicación de $L_{\emptyset}$ en la jerarquía de la computabilidad?

## 6. Sea el lenguaje $D_{HP} = \lbrace w_i \mid M_i \text{ para a partir de } w_i \rbrace$ (considerar el orden canónico}. Encontrar una reducción de $D_{HP}$ a $HP$. Comentario: hay que definir la función de reducción y probar su total computabilidad y correctitud.

## 7. Sean $TAUT$ y $NOSAT$ los lenguajes de las fórmulas booleanas sin cuantificadores tautológicas (satisfactibles por todas las asignaciones de valores de verdad) e insatisfactibles (ninguna asignación de valores de verdad las satisface), respectivamente. Encontrar una reducción de $TAUT$ a $NOSAT$. Comentario: hay que definir la función de reducción y probar su total computabilidad y correctitud.

## 8. Se prueba que existe una reducción de $L_U^C$ a $L_{\Sigma^*}$ (y así, como $L_U^C \notin RE$, entonces se cumple que $L_{\Sigma^*} \notin RE$). La reducción es la siguiente. Para toda $w: f(( \langle M_1 \rangle, w)) = \langle M_2 \rangle$, tal que $M_2$, a partir de su entrada $v$, ejecuta $|v|$ pasos de $M_1$ a partir de $w$, y acepta sii $M_1$ no acepta. Probar que la función definida es efectivamente una reducción de $L_U^C$ a $L_{\Sigma^*}$ (es total computable y correcta).
