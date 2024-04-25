Slide aggiornate [[CAT_parte2_2023_10_11.pdf]]

L'evoluzione libera di un LTI è:

$$
\dot x(t) = A x(t)
$$

Ricordiamo come sono fatti gli *equilibri* di un sistema lineare tempo invariante:

In generale$f(x) := Ax$, e sappiamo che gli equilibri sono $f(x_E) = 0$, quindi
$$A x_e = 0$$
In particolare $x_e = 0$ è **sempre** un equilibrio del sistema.

## Proprietà di sistemi LTI

> [!warning] Proprietà: *Stabilità di un sistema LTI*
> Tutti gli equilibri (e tutte le traiettorie) di un sistema LTI hanno la stessa proprietà di stabilità di $x = 0$. 
> 
> Parleremo quindi di **stabilità del sistema**


Se io studio le prop. di stabilità di origine di un LTI, esse valgono per tutti gli equilibri.

**Stabilità di un *equilibrio*** $\Longrightarrow$ **Stabilità di un sistema**

## Stabilità interna di sistemi LTI

> [!error] Teorema: *Stabilità asintotica di un sistema LTI*
> Un sistema LTI è asintoticamente stabile ***se e solo se*** tutti gli autovalori hanno *parte reale (strettamente) negativa* ($< 0$).
> 
> *[[CAT_parte2_2022_09_20.pdf#page=89&selection=27,7,33,2|CAT_parte2_2022_09_20, page 89]]*

> [!tip] Definizione: *Marginalmente stabile*
> Stabile ma non asintoticamente stabile

> [!info] Teorema: *Stabilità marginale di un sistema LTI*
> Un sistema LTI è stabile **se e solo se**
> - tutti gli autovalori hanno parte reale minore o uguale a zero e 
> - tutti gli autovalori a parte reale nulla hanno molteplicità geometrica uguale alla molteplicità algebrica (i mini-blocchi di Jordan associati hanno dimensione uno).
> 
> *[[CAT_parte2_2022_09_20.pdf#page=89&selection=34,0,39,69|CAT_parte2_2022_09_20, page 89]]*


### Come trovare la stabilità di un sistema LTI
Calcolo gli autovalori della matrice A.
- Se sono a parte reale negativa, è stabile.
- Altrimenti devo capire cosa succede.


### Osservazione 1
La stabilità di sistemi LTI è **sempre globale**. (*vedi onenote*)

### Osservazione 2
Se un sistema LTI è (globalmente) asintoticamente stabile, allora $x = 0$ è l'unico equilibrio.

  > [!info] Nota 
  > Anche per sistemi non lineari, se $x_e$ è G.A.S (globalmente asintoticamente stabile) allora è l'unico equilibrio.
  > 
  > Se il mio equilibrio è *globalmente* attrattivo deve per forza essercene uno.


$x=0$ c'è per forza. Se è GAS non ce ne possono essere altri.

m.a. = m.g. -> tutti i blocchi di Jordan di dimensione 1


Next: [[2.2 - Controllo]]