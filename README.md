Instancia C - Salud

Integrante: Eyleen Spencer Yates
Integrante: Sebástian Ibarra Vera

# Equipo C
# Salud. Abastecimiento de insumos

> ## 1.- Construya la red expandida en el tiempo: un nodo por cada par (ubicación, mes), arcos de adquisición, arcos de envío y arcos de inventario que unen un mes con el siguiente. Incluya el diagrama de la red en su cuaderno de resultados.  



![images/red_instancia_C.png]

> ## 2.- Formule el modelo y resuélvalo. Informe el plan de compras, los envíos y el inventario al cierre de cada mes.  

La función objetivo suma cuatro tipos de costos. Primero, el costo de adquisición, que corresponde a multiplicar la cantidad comprada en cada mes por el precio de compra de ese mes y luego sumar los tres meses. Segundo, el costo de transporte, que corresponde a multiplicar las dosis enviadas a cada centro por el costo unitario de envío hacia ese centro y sumar todos los envíos realizados en los tres meses. Tercero, el costo de almacenamiento en el laboratorio, que se calcula multiplicando las dosis que quedan guardadas al cierre de cada mes por el costo de mantener una dosis almacenada durante un mes. Cuarto, el costo de almacenamiento en los centros, que se calcula de la misma manera, multiplicando las dosis que permanecen guardadas en cada centro por el costo de almacenamiento correspondiente, lo que corresponden a la tabla dado para el caso C. `Seba si quieres complementar la respuesta puedes poner cuales son las función objetivo y restricciones que te mandé escritas y no programadas.`
El modelo compra primero todo lo posible en el mes 1 porque es el período más barato: adquirir una dosis cuesta $\$3.100$. Como la capacidad máxima de compra es de 2.400 dosis, llega a ese límite. Luego utiliza al máximo el mes 2, donde la dosis cuesta $\$3.400$, porque sigue siendo más conveniente que comprar en el mes 3, donde cuesta $\$3.900$.
Aunque anticipar compras genera almacenamiento, sigue siendo económicamente favorable: una dosis comprada en el mes 2 y almacenada un mes en el laboratorio cuesta $\$3.400$ + $\$90$ = $\$3.490$, todavía menor que los $\$3.900$ del mes 3. Una dosis comprada en el mes 1 y almacenada dos meses cuesta $\$3.100$ + $\$180$ = $\$3.280$, también inferior a comprarla directamente en el mes 3.
Por eso el óptimo concentra las compras en los meses 1 y 2, con 2.400 dosis en cada uno, y deja para el mes 3 sólo las 1.200 dosis restantes. Además, el costo de almacenamiento en los centros es cero porque en la solución óptima no queda inventario almacenado en R1 ni en R2 al cierre de los meses: las dosis enviadas a los centros se utilizan directamente para cubrir su demanda. Como el almacenamiento en el laboratorio cuesta $\$90$ por dosis-mes y en los centros cuesta $\$140$, al modelo le conviene mantener el inventario anticipado en el laboratorio mientras exista capacidad disponible allí. Por eso el inventario en centros es cero y, en consecuencia, también su costo de almacenamiento
El costo de adquisición es de $\$20.280.000$, porque corresponde a comprar 2.400 dosis a $\$3.100$, 2.400 a $\$3.400$ y 1.200 a $\$3.900$. El costo de transporte es de $\$3.608.000$, considerando todos los envíos realizados a R1 y R2 durante los tres meses. El costo de almacenamiento en el laboratorio es de $\$180.000$, porque se mantienen 800 dosis al cierre del mes 1 y 1.200 dosis al cierre del mes 2, a $\$90$ por dosis-mes. El costo de almacenamiento en los centros es $\$0$, porque en la solución óptima no queda inventario almacenado en R1 ni en R2: lo que se envía se utiliza para cubrir directamente la demanda, y además almacenar en el laboratorio es más barato que en los centros.

Sumando estos cuatro costos, $\$20.280.000$ de adquisición + $\$3.608.000$ de transporte + $\$180.000$ de almacenamiento en laboratorio + $\$0$ de almacenamiento en centros, se obtiene el costo óptimo total de $\$24.068.000$.


> ## 3.- Compare el costo óptimo con la política ingenua de comprar cada mes exactamente lo que ese mes se consume. Cuantifique el ahorro y explique de dónde proviene.  

La política ingenua consiste en adquirir exactamente lo que se consume cada mes: 1.600 dosis en el mes 1, 2.000 en el mes 2 y 2.400 en el mes 3. Con eso, el costo de adquisición es $\$21.120.000$. El costo de transporte se mantiene en $\$3.608.000$, porque la cantidad total de dosis enviadas a los centros no cambia. En cambio, el costo de almacenamiento pasa a ser $\$0$, ya que no se guarda inventario. Por lo tanto, el costo total es $\$24.728.000$, es decir, $\$660.000$ más caro que la solución óptima, equivalente a aproximadamente 2,67% más.

La lógica de esa diferencia es que, al no aprovechar al máximo los meses más baratos, se obliga al modelo a comprar más en el mes 3, que es el más caro. En el mes 1 se dejan de anticipar 800 dosis; cada una termina costando \$620 más, porque comprarla en el mes 3 cuesta $\$3.900$, mientras comprarla en el mes 1 y almacenarla dos meses cuesta $\$3.100 + \$90 + \$90 = \$3.280$. Eso genera $\$496.000$ adicionales (620*800). Además, en el mes 2 se dejan de anticipar 400 dosis; cada una cuesta $\$410$ más, porque $\$3.900 − (\$3.400 + \$90) = \$410$. Eso agrega $\$164.000$ ($410\times400$). La suma de ambos efectos es exactamente $\$660.000$.


> ## 4.- Determine el valor de una unidad adicional de capacidad de adquisición en cada uno de los tres meses. Los tres valores son distintos y uno de ellos es cero: interprete cada caso.  
Para determinar el valor de una unidad adicional de capacidad de adquisición, se analiza cuánto se podría ahorrar si en cada mes fuera posible comprar una dosis más que el límite actual de 2.400 dosis.

En el mes 3 el valor es $\$0$, porque en la solución óptima solamente se compran 1.200 dosis, aunque la capacidad permite comprar hasta 2.400. Por lo tanto, existe capacidad disponible y aumentar el límite a 2.401 no genera ningún beneficio, ya que esa dosis adicional no sería necesaria.

En el mes 2, comprar una dosis cuesta $\$3.400$, mientras que en el mes 3 cuesta $\$3.900$, por lo que comprarla anticipadamente permite inicialmente ahorrar $\$500$. Sin embargo, para utilizar esa dosis adicional en el mes 3 es necesario almacenarla. Como la bodega del laboratorio ya se encuentra en su capacidad máxima, la dosis marginal debe almacenarse en un centro, con un costo de $\$140$. Por lo tanto, el beneficio de aumentar la capacidad del mes 2 en una dosis es $\$500 - \$140 = \$360$ por dosis.

En el mes 1, una dosis cuesta $\$3.100$ frente a los $\$3.900$ del mes 3, por lo que comprarla anticipadamente permite inicialmente ahorrar $\$800$. Sin embargo, esa dosis debe almacenarse durante los dos períodos siguientes: primero en el laboratorio, con un costo de $\$90$, y luego en un centro, con un costo de $\$140$, porque la capacidad de almacenamiento del laboratorio ya está completamente utilizada para el paso hacia el mes 3. Por lo tanto, el valor de aumentar la capacidad del mes 1 en una dosis es $\$800 - \$90 - \$140 = \$570$ por dosis.

De esta forma, el valor de una unidad adicional de capacidad es $\$570$ en el mes 1, $\$360$ en el mes 2 y $\$0$ en el mes 3. Los valores son distintos porque dependen de cuánto se puede ahorrar comprando antes y de los costos adicionales de almacenamiento necesarios para trasladar esa dosis hacia el mes en que será consumida.


> ## 5.- Obtenga los valores duales de los nodos del laboratorio en los tres meses y explique la relación aritmética que guardan entre sí.  

**Valores obtenidos** (en \$/dosis, interpretados como el valor de disponer de una dosis en el laboratorio en ese mes):

| Nodo | $\pi_i$ (\$/dosis) | Costo de adquisición | Valor marginal de capacidad (pregunta 4) |
|---|---:|---:|---:|
| $Lab_1$ | 3.670 | 3.100 | 570 |
| $Lab_2$ | 3.760 | 3.400 | 360 |
| $Lab_3$ | 3.900 | 3.900 | 0 |

La primera relación que se observa es que el dual de cada nodo descompone exactamente en los dos términos de la pregunta anterior:

$$\pi_{Lab_t} \;=\; c^{adq}_t \;+\; v_t$$

donde $c^{adq}_t$ es el precio de compra del mes $t$ y $v_t$ el valor de una unidad adicional de capacidad de adquisición en ese mes. Esto no es coincidencia: $v_t$ es precisamente el costo reducido (en valor absoluto) del arco $F \to Lab_t$, es decir la diferencia entre lo que vale una dosis en ese punto de la red y lo que cuesta ponerla ahí.

**a) La relación entre los tres duales.** Tomando las diferencias consecutivas:

$$\pi_{Lab_2} - \pi_{Lab_1} = 3.760 - 3.670 = 90 = h_{lab}$$

$$\pi_{Lab_3} - \pi_{Lab_2} = 3.900 - 3.760 = 140 = h_{centro}$$

El valor de una dosis **aumenta** conforme avanza el horizonte, y el incremento mes a mes es exactamente el costo de almacenarla de un período al siguiente. Pero el costo relevante **no es el mismo en los dos tramos**, y esa es la parte interesante de la respuesta.

**b) Por qué el primer salto es 90 y el segundo es 140.** La condición de optimalidad exige que todo arco con flujo estrictamente entre sus cotas tenga costo reducido nulo, es decir $\pi_j - \pi_i = c_{ij}$. Lo que determina el salto es cuál es la ruta de almacenamiento **disponible en el margen**:

| Tramo | Arco de bodega del laboratorio | Estado | Ruta marginal | Salto |
|---|---|---|---|---:|
| Mes 1 → 2 | 800 de 1.200 | con holgura | bodega del laboratorio ($h_{lab}=90$) | 90 |
| Mes 2 → 3 | 1.200 de 1.200 | saturado | bodega del centro ($h_{centro}=140$) | 140 |

Entre los meses 1 y 2 la bodega del laboratorio tiene capacidad sobrante (se usan 800 de 1.200), así que una dosis marginal se guarda ahí y el salto es 90. Entre los meses 2 y 3 la bodega del laboratorio está completamente ocupada, de modo que una dosis marginal solo puede trasladarse almacenándola en un centro, y el salto pasa a ser 140. Esto se verifica en el costo reducido del arco $R1_2 \to R1_3$:

$$\bar c_{R1_2 \to R1_3} = h_{centro} + \pi_{R1_2} - \pi_{R1_3} = 140 + 4.240 - 4.380 = 0$$

Un arco con flujo cero y costo reducido cero significa que está justo en el punto de indiferencia: es la alternativa que fija el precio en el margen, aunque no se use en el óptimo.

**c) De dónde sale el nivel.** El valor de $\pi_{Lab_3}$ ancla toda la cadena. El mes 3 es el único que **no satura** su capacidad de adquisición (compra 1.200 de 2.400 disponibles), por lo que es la fuente de reserva del sistema: cualquier dosis adicional que el sistema necesite se compra ahí, al precio de 3.900. De ahí que $\pi_{Lab_3} = c^{adq}_3 = 3.900$, y los otros dos se obtengan retrocediendo:

$$\pi_{Lab_2} = \pi_{Lab_3} - h_{centro} = 3.900 - 140 = 3.760$$

$$\pi_{Lab_1} = \pi_{Lab_2} - h_{lab} = 3.760 - 90 = 3.670$$

**d) Interpretación.** El dual de $Lab_t$ mide cuánto vale tener una dosis disponible en el laboratorio en el mes $t$, medido contra la alternativa de comprarla al precio más caro del horizonte. Una dosis vale menos cuanto antes esté disponible, porque hay que pagar por conservarla hasta el momento de consumo, y esa pérdida de valor es exactamente el costo de almacenamiento de la ruta que esté disponible en el margen. Es una condición de no arbitraje: si el salto fuera mayor que el costo de guardar, convendría almacenar más; si fuera menor, convendría almacenar menos. En el óptimo ninguna de las dos modificaciones mejora el costo total.

**e) Dos advertencias sobre estos valores.**

*La solución dual es degenerada.* El salto del segundo tramo puede tomar cualquier valor en el intervalo $[h_{lab},\, h_{centro}] = [90,\, 140]$ y seguir siendo dualmente óptimo. Los valores reportados corresponden al extremo superior, que es el que reproduce los valores marginales de la pregunta 4; otro solver, u otra corrida, podría entregar el extremo inferior.

*Consecuencia aparentemente contradictoria.* Con estos duales, el arco de bodega del laboratorio entre los meses 2 y 3 tiene costo reducido

$$\bar c_{Lab_2 \to Lab_3} = h_{lab} + \pi_{Lab_2} - \pi_{Lab_3} = 90 + 3.760 - 3.900 = -50,$$

lo que sugeriría que una unidad adicional de bodega ahorraría \$50. Sin embargo, al resolver nuevamente con capacidad 1.201 el ahorro es \$0 (Paso 8). No hay contradicción: con los meses 1 y 2 ya saturados en compra, no existe ninguna dosis extra que guardar, de modo que esa capacidad adicional no puede aprovecharse. Es precisamente el motivo por el que conviene obtener los valores marginales resolviendo nuevamente el modelo, en vez de leerlos directamente del dual.


> ## 6.- Si la capacidad de adquisición bajara a 2.000 dosis mensuales, ¿el plan sigue siendo factible? ¿En cuánto aumenta el costo?  

Sí, sigue siendo factible.  
La capacidad total pasa a ser $3 \times 2.000 = 6.000$ dosis, exactamente igual a la demanda total del horizonte (6.000), así que el laboratorio queda obligado a comprar el tope los tres meses, sin ningún margen. La factibilidad depende de que la bodega del laboratorio (1.200 de capacidad) alcance para el inventario que hay que arrastrar, y además alcanza, con holgura, ya que el nuevo plan solo necesita guardar 400 dosis de un mes a otro.

Nuevo costo óptimo: $\$24.480.000$ $\rightarrow$ aumento de $\$412.000$

| Mes | Compra | Envío R1 | Envío R2 | Inventario lab. al cierre |
|---|---:|---:|---:|---:|
| 1 | 2.000 | 900 | 700 | 400 |
| 2 | 2.000 | 1.400 | 600 | 400 |
| 3 | 2.000 | 1.100 | 1.300 | 0 |




## Estructura del repositorio

```
.
├── README.md                              # este archivo
├── datos/
│   ├── demanda.csv
│   └── parametros.csv
├── Taller_1_InstanciaC.ipynb     # modelo completo (Pyomo + HiGHS) + Respuestas (también escritas en este documento).
```

