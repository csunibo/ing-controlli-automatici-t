PDF: [[CAT_parte2_2023_10_11.pdf]]

Quando parleremo di un sistema parleremo di **una ODE ==ASTRATTA==**, perchè descrive il comportamento nel tempo di un sistema.

Questo perchè $t \in \mathbb R$.


> [!warning] Importante
> Non vogliamo controllare **SOLO** il circuito elettrico. Voglio trovare un SET di equazioni ODE generali, tali per cui **il modello può essere applicato su vari casi**.


>[!warning] Notazione
>Con il punto indichiamo **sempre** le derivate **rispetto al tempo**

## Forma di stato

Sistemi in **forma di stato**: un sistema che descriviamo con due equazioni:
- l'equazione **di stato** (una ODE **del primo ordine**)
- l'equazione **di uscita** (una equazione algebrica)

$x(t) \in \mathbb R^n$: **stato** del sistema all'istante $t$
$u(t) \in \mathbb R^m$: **ingresso** del sistema all'istante $t$
$y(t) \in \mathbb R^p$ : **uscita** del sistema all'istante $t$

*Vedi onenote "Sistemi in forma di stato"*

> [!warning] Attenzione
> Ricorda che **l'equazione di stato** è un **equazione vettoriale**, ovvero **è composta da $n$ componenti**.

> [!warning] Attenzione
> Per noi ogni componente dello stato **è uno scalare**.
>
> Se ho un vettore devo scomporlo in più variabili di stato.

### Stato iniziale

Abbiamo bisogno però anche l'**inizializzazione** del sistema, ovvero lo **stato iniziale**

>[!tldr] Stato iniziale
> $$x(t_0) = x_0$$
> $t_0$: tempo iniziale


>[!question] E' limitante il fatto che ci sia solo il primo ordine?
>
> **NO**, perchè abbiamo un vettore di ODE del primo ordine e possiamo legarle da derivate, quindi derivata prima di derivata prima = derivata seconda.

### Sistemi causali

> Se la soluzione x(t) a partire da un istante iniziale $t_0$ è univocamente determinata da $x(t_0)$ e $u(\tau), τ \ge t_0$, allora il sistema è detto **causale**.
>
> [[CAT_parte2_2022_09_20.pdf#page=8&selection=3,1,41,16|CAT_parte2_2022_09_20, page 8]]

*Ovvero la soluzione non dipende dagli ingressi futuri del sistema, ovvero è un sistema realizzabile fisicamente.*

Per i sistemi causali, sotto opportune ipotesi di regolarità della funzione $f$, **si dimostra l'esistenza e l'unicità della soluzione dell'eq. di stato**.
### Sistemi discreti

La variabile **tempo è un numero intero**.

L'equazione di stato non è differenziale, ma è una **equazione alle differenze finite (FDE)**.

##### Esempi
- pipeline di un processore o di un processo di produzione, intrinsecamente discreti
- tutti gli algoritmi sono sistemi discreti
- per usare tool devo lavorare in discreto oppure chiedere ai tool adeguati


### Esempio: circuito elettrico slide 7

#### Sensore che misura $v_R(t)$
La leggo e la chiamo **uscita** del sistema.

$$y(t) = u(t)-x(t)$$

>[!warning]
>In questo caso potrei ricavare lo stato dalle variabili di uscita, **ma questa cosa non è detta**.

### Esempio: carrello - slide 8

Ipotizziamo un **centro di massa**. Le forze agiscono sul centro di massa.

### Esempio: auto in rettilineo - slide 9

### Esempio: pendolo - slide 11

## Traiettoria di un sistema
E' una particolare funzione del tempo $(x(t), u(t))$ che deve soddisfare l'equazione di stato.

- $x(t)$ traiettoria di stato
- $y(t)$ traiettoria dell'uscita

> [!warning] Nota
> Per sistemi **senza ingresso** (non forzati) la traiettoria $x(t), t \ge t_0$ è determinata solo dallo stato iniziale $x_{t_0}$

##### Come ottenerla facilmente?
1. Scegliamo un ingresso
2. Integriamo

> [!tip] Obiettivo
> Avere uno **stato desiderato** e capire **quali uscite dare** per fare in modo di ottenerlo.
###  Equilibrio di un sistema di controllo
*Vedi slide, pagina 13*

### Coppia di equilibrio

$(x_e, u_e)$ è una coppia di equilibrio se

$x(t_0) = x_e$
$u(t) = u_e, \quad\forall t \ge t_0$

allora

$x(t) = x_e, \forall t \ge t_0$

*Vedi "equilibri del pendolo" su OneNote*

### Proprietà sistemi tempo invarianti continui
Data una coppia di equilibrio $(x_e, u_e)$, vale che
$$f(x_e, u_e) = 0$$

## *Richiami di calcolo matriciale*  $\nearrow$

# Classificazione di sistemi in forma di stato

L'ideale sarebbe ottenere una $f$ ed una $h$ assolutamente generiche. Il problema è che più teniamo generali ste due funzioni, meno possiamo dire.

Quindi prendiamo delle **sottoclassi** e le analizziamo.
- SISO (Single Input Single Output)
- MIMO (Multiple Input Multiple Output)

## Sistemi **monovariabili** (SISO)

Lo stato ha una generica dimensione $n$, ma l'ingresso e l'uscita hanno **dimensione 1**.

$y \in \mathbb R$
$u \in \mathbb R$

## Sistemi **strettamente propri**

*Proprio* $\sim$ Causalità

- **Propri**
- **Strettamente propri**: quando l'equazione di uscita non dipende dall'ingresso.

> [!tip]
> Nel caso di un sistema strettamente proprio una **discontinuità** in ingresso non determina una discontinuità in uscita.


## Sistemi forzati
- **Non forzati**: quando non ha un ingresso
- **Forzati**: quando ha un ingresso

Fissata la $x(t_0) = x_0$ il sistema procederà allo stesso modo ogni volta (considerando che la $f$ considera anche il disturbo come funzione del tempo).


> [!warning] Nota
> Sceglieremo $u(t)$ come "funzione di $x(t)$ o $y(t)$".
>
> Preferibilmente dalla $y(t)$ visto che la $x(t)$ in generale è non nota.

## Sistemi tempo **invarianti**

sistemi tempo **invarianti** $\subset$ sistemi tempo **varianti**

*Vedi onenote per i grafici*

> Tempo invarianti

[[CAT_parte2_2022_09_20.pdf#page=32&selection=70,0,70,16|CAT_parte2_2022_09_20, page 32]]

Data una traiettoria $(x(t), u(t)), t > 0$, $\forall \Delta \in \mathbb R$ vale che per $x(t_0+\Delta) = x_0$, allora $(x_\Delta(t), U_\Delta(t)) = (x(t-\Delta), u(t-\Delta))$ è una traiettoria.

>[!tip] Non dipendenza dal tempo
>Si dimostra che un sistema è tempo invariante *se e solo se*, le funzioni $f$ e $h$ **non dipendono esplicitamente dal tempo**.
>
>$$ (x,u) \longmapsto f(x,u)$$

>[!info]
>**Per sistemi tempo invarianti** prenderemo, senza perdere generalità, $$t_0 = 0$$

## Sistemi lineari
Un sistema sotto forma di stato è **lineare** se e solo se:
- la funzione di stato  $f$ è **lineare** in $x$ e in $u$
- la funzione di uscita $h$ è **lineare** in $x$ e in $u$

> [!tip] Coppia di equilibrio per un **sistema lineare**
>
> $(0,0)$ è sempre un equilibrio per un sistema lineare.
>
> Quindi, **nei sistemi lineari c'è sempre almeno una coppia di equilibrio**, essendo che la funzione è lineare e quindi lo 0 va in 0.

### Rappresentazione matriciale

Se il sistema è **lineare** posso rappresentarlo in maniera **matriciale**.

> [!error] Questa è una notazione compatta!!!!

$$
\dot x(t) = A(t)x(t) + B(t)u(t)
$$
$$
\dot y(t) = C(t)x(t) + D(t)u(t)
$$

$$
A(t) = \begin{bmatrix}
	a_{11}(t) & \dots  & a_{1n}(t) \\
	\vdots    & \ddots & \vdots    \\
	a_{n1}(t) & \dots  & a_{nn}(t)
\end{bmatrix}
\
B(t) = \begin{bmatrix}
	b_{11}(t) & \dots  & b_{1m}(t) \\
	\vdots    & \ddots & \vdots(t) \\
	b_{n1}(t) & \dots  & b_{nm}(t)
\end{bmatrix}
\
C(t) = \begin{bmatrix}
	c_{11}(t) & \dots  & c_{1n}(t) \\
	\vdots    & \ddots & \vdots \\
	c_{p1}(t) & \dots  & c_{pn}
\end{bmatrix}
\
D(t) = \begin{bmatrix}
	d_{11}(t) & \dots  & d_{1n}(t) \\
	\vdots    & \ddots & \vdots \\
	d_{p1}(t) & \dots  & d_{pm}
\end{bmatrix}
$$

$$
\begin{bmatrix}
	\dot x_1(t) \\
	\vdots      \\
	\dot x_n(t)
\end{bmatrix} =
\begin{bmatrix}
	a_{11}(t) & \dots  & a_{1n}(t) \\
	\vdots    & \ddots & \vdots    \\
	a_{n1}(t) & \dots  & a_{nn}(t)
\end{bmatrix}
\begin{bmatrix}
	x_1(t) \\
	\vdots \\
	x_n(t)
\end{bmatrix}
+
\begin{bmatrix}
	b_{11}(t) & \dots  & b_{1m}(t) \\
	\vdots    & \ddots & \vdots \\
	b_{n1}(t) & \dots  & b_{nm}(t)
\end{bmatrix}
\begin{bmatrix}
	u_1(t)	\\
	\vdots \\
	u_m(t)
\end{bmatrix}
$$

> [!tip]
> Il modello del sistema è **completamente descritto** da 4 matrici!


**Attenzione alla grandezza delle matrici!**
- $A(t) \in \mathbb R^{n\times n}$
- $B(t) \in \mathbb R^{n\times m}$
- $C(t) \in \mathbb R^{p\times n}$
- $D(t) \in \mathbb R^{p\times m}$

Nel caso di sistemi SISO, avremo una particolare struttura.

### Sistema lineare tempo invariante

$$\dot x(t) = Ax(t) + Bu(t)$$
$$y(t)=Cx(t)+Du(t)$$

Le matrici $A,B,C,D$ non dipendono dal tempo (e.g. sono **costanti**).


### Sistema lineare SISO

Nei sistemi lineari SISO ($m = 1, p = 1$)
- la matrice B è un vettore riga ($n \times 1$)
- la matrice C è un vettore colonna ($1 \times n$)
- la matrice D è uno scalare ($1 \times 1$)


## Principio di sovrapposizione degli effetti

> [!error] Vale solo per i **sistemi lineari**! (anche tempo varianti)

Se prendo una *combinazione lineare* degli stati iniziali e  la **stessa** combinazione lineare di traiettorie, **ottengo come traiettoria la combinazione lineare delle traiettorie**.

*[[CAT_parte2_2022_09_20.pdf#page=42|Vedi slides]]*

$\forall \alpha,\beta \in \mathbb R$, dato lo stato iniziale $x_{ab}(t_0) = \alpha x_{0_{a}} + \beta x_{0_{b}}$ si ha che
$$
(x_{ab}(t),u_{ab}(t)) = (\alpha x_a(t) + \beta x_b(t), \alpha u_a(t)+\beta u_b(t))
$$
è una traiettoria del sistema.

*Per chi vuole c'è la dimostrazione a pag 43 (materiale aggiuntivo)*

### Scomposizione di un'evoluzione di un sistema lineare in evoluzione forzata ed evoluzione libera

*Vedi onenote per dettagli: "Scomposizione di un sistema lineare"*

Considero due traiettorie di stato, quella ottenuta

|  | $x_l(t)$ | $x_f(t)$ |
| ---- | ---- | ---- |
| Stato iniziale | $x_0$ | $0$ |
| Ingresso | $0$ | $u(t)$ |
|  | Evoluzione **libera** | Evoluzione **forzata** |
Ogni evoluzione di un sistema lineare si può scrivere come la somma di
- un'**evoluzione libera**
- un'**evoluzione forzata**

Entrambe le evoluzioni valgono dallo **stesso istante iniziale**. Quindi *fisicamente* dovrei fare gli esperimenti in *contemporanea*.

>[!tip]
>La stessa cosa vale per le uscite, ovvero
>$$ y(t) = y_l(t) + y_f(t) $$

## Evoluzione libera di un LTI

Quando studio l'evoluzione libera del sistema, ne studio la componente $Ax(t)$

## Traiettorie: LTI esempio scalare

*Vedi pagina 48*

## Traiettorie: LTI caso generale

In generale so che quindi l'evoluzione dello stato di un sistema è dato da
- un **esponenziale** che rappresenta l'evoluzione libera
- un **integrale di convoluzione** che rappresenta l'evoluzione forzata

> [!warning] Importante
> Nel caso dell'evoluzione libera, **tutto il comportamento del sistema è rappresentato dalla matrice $A$**.


## Esponenziale di matrice

$$
e^{At} := I + At + \frac{(At)^2}{2!} + \frac{(At)^3}{3!} + \dots
$$

## Proprietà della matrice esponenziale

### Esponenziale e cambio di base

$$
e^{TAT^{-1}t} = Te^{At}T^{-1}
$$

### Esponenziale di una matrice diagonale a blocchi

> L’esponenziale di una matrice diagonale a blocchi è una matrice diagonale a blocchi in cui ogni blocco è l’esponenziale del blocco corrispondente della matrice di partenza.

[[CAT_parte2_2022_09_20.pdf#page=50&selection=22,0,25,69|CAT_parte2_2022_09_20, page 50]]

## Modi naturali del sistema (LTI)

L'**evoluzione libera** di un ***sistema lineare tempo invariante*** sarà un vettore dove tutte le componenti sono *combinazioni lineari* di:
$$
t^q e^{\lambda t}
$$
- con $\lambda$ autovalori della matrice $A$.
- con eventualmente $\lambda \in \mathbb C$

I termini $t^q \ e^{\lambda t}$ sono detti **modi naturali** del sistema.

>[!tldr] Ricorda
>L'**evoluzione libera** dello stato è **combinazione lineare dei modi**.

> [!info] Evoluzione libera dell'uscita
> Poichè l'uscita è lineare nello stato, anche l'**evoluzione libera dell'uscita** è combinazione lineare dei modi

Gli autovalori possono essere
- reali
- complessi coniugati

> [!warning] Perchè?
> Si dimostra che un polinomio a coefficienti tutti reali ha radici reali o complessi coniugati.

> Si dimostra che i coefficienti γjiq corrispondenti a λi e ¯λi sono anch’essi complessi coniugati.

[[CAT_parte2_2022_09_20.pdf#page=56&selection=109,0,125,35|CAT_parte2_2022_09_20, page 56]]

**Si verifica** quindi per calcolo diretto che le soluzioni $x_{l,j} (t)$ sono sempre reali e che i modi del sistema corrispondenti ad autovalori complessi coniugati $\lambda_i = \sigma_i + j\omega_i$ e $\bar \lambda_i$ sono del tipo:
 $$t^{q-1}e^{\sigma_i t} cos(\omega_i t + \phi_i)$$
con opportuni valori della fase $\phi_i$.

[[CAT_parte2_2022_09_20.pdf#page=56&selection=126,0,157,13|CAT_parte2_2022_09_20, page 56]]

### Caso molteplicita algebrica = molteplicita geometrica

Supponiamo che le **molteplicità algebriche** $n_1, \dots, n_r$ degli autovalori di $A$ coincidano con le **molteplicità geometriche** (ad es quando gli **autovalori sono distinti**).

**Si dimostra che** i coefficienti $h_i$ sono tutti pari ad $1$ e l'espressione dei modi si semplifica in

| Modo | Autovalore |
| ---- | ---------- |
| $e^{\lambda_i t}$  | Reale |
| $e^{\sigma_i t} \cos(\omega_i t + \omega_i)$ | Complesso coniugato |

> [!info] Molteplicità algebrica
> Grado con cui si trova l'autovalore nel polinomio caratteristico

> [!info] Molteplicità geometrica
> Grandezza dell'autospazio di quell'autovalore
#### Autovalori reali semplici ($\Im(\lambda) = 0$)

$\lambda > 0$ -> sistema **diverge**
$\lambda = 0$ -> sistema **stabile**
$\lambda < 0$ -> sistema **converge** a stabilità


### Caso generale

### Autovalori reali con m.a > m.g

$t^q \ne 0$

$\lambda > 0$: diverge comunque
$\lambda  = 0$: dipende dal valore di $t^q$. Può divergere. Diverge come un polinomio in $t$, non come un esponenziale though.
$\lambda < 0$: gli esponenziali vanno a zero più velocemente dei polinomi. Nella parte iniziale predomina la parte divergente, poi però la funzione va a zero.

> [!warning] Occhio al transitorio!
> Per $lambda < 0$ devo stare attento al transitorio!

### Autovalori complessi coniugati con m.a. > m.g.

$\sigma_i > 0$: diverge comunque. Va ad infinito sinusoidalmente.
$\sigma_i = 0$: come nel caso precedente, dipende dal valore di $t^q$. Può divergere. Diverge come un polinomio in $t$, non come esponenziale.
$\sigma_i = 0$: crescita iniziale. Dopo un po' l'esponenziale predomina ma poi mi porta il segnale a zero.

> [!error] Attenzione ai $\sigma_i$!
> Sia per $\sigma_i > 0$ che per $\sigma_i = 0$ devo stare attento, perchè nel primo caso diverge, nel secondo caso PUO' divergere.

### Esempio: carrello (pag 47)

*Esempio con controllo su onenote*

Nel caso di $h^2 = 4Mk$, la molt algebrica è 2 e si dimostra che la molt. geom. = 1.


> [!warning]
> Se la $u(t)$ è solo funzione dello stato possiamo considerare il sistema come comunque "ad evoluzione libera".

## Equilibrio: richiami per sistemi tempo invarianti continui

Se $(x_e, u_e)$ è una **coppia di equilibrio**
- $f(x_e, u_e) = 0$ (ricordiamo che $f$ è la *derivata*)


Se il sistema non è forzato
- $f(x_e) = 0$

Ricordiamoci che il nostro sistema è un **modello della realtà**, quindi non avrò mai un ingresso e uno stato iniziale *ideali (posti ad un valore noto e certo)*.

Cosa succede quando supponiamo che esistano **perturbazioni** sullo *stato iniziale*?

## Stabilità interna

***Interna*** perchè dipende da variazioni di variabili interne del sistema (ovvero dello stato).

- #### ==Equilibrio **stabile**==
	*Partendo da vicino all'equilibrio rimaniamo vicino all'equilibrio*
	*Vedi slides per definizione rigorosa.*

- #### Equilibrio **instabile**
	Uno stato di equilibrio **NON** stabile.

- #### Equilibrio **attrattivo**
	$\exists \ \delta > 0, \quad \forall x_0: ||x_0 - x_e|| \le \delta$ 	allora risulta che $$lim_{t \to \infty}||x(t) - x_e|| = 0$$
	osservazioni:
	1. è $t \to \infty$, quindi posso farmi anche il giro del mondo prima di collassare sull'equilibrio
	2. esiste **ALMENO** un delta, non per ogni epsilon, ovvero non è detto che io rimanga in un intorno definito

	quindi, **non è detto sia stabile**

- #### ==Equilibrio asintoticamente stabile==
	E' contemporaneamente
	- **stabile**
	- **attrattivo**

### Osservazioni

- Stabilità **locale**
	*In un intorno dello stato di equilibrio $x_e$*

- Stabilità **globale**
	*Se valgono $\forall x \in \mathbb R^n$*

- Stabilità **di una traiettoria**
	*Le definizioni di stabilità si possono generalizzare ad una traiettoria $\bar x(t), t \ge 0$*

	In generale si considera la stabilità di uno stato come nel caso della traiettoria ma con una *costante* come traiettoria.


Next: [[2.1 - Sistemi lineari tempo invariante]]
