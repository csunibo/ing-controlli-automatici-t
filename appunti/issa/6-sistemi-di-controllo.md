Fondamento dei sistemi di controllo è la **retroazione**, ovvero decido istante per istante che ingresso dare al mio sistema sulla base di quello che leggo sull'uscita.

## Sistema in retroazione

*Vedi su onenote lo schema di un caso ideale: senza rumori e/o disturbi*

## Disturbi e rumori

*Vedi onenote*

## Schema di controllo in retroazione

> [!tip] Funzione di trasferimento in anello aperto
> $$L(s) = R(s) G(s)$$

Se rompessimo la retroazione avremmo questa funzione di trasferimento.

> [!warning] Attenzione
> Chiamiamo $y_{RIF} = w$ per comodità
## Schema semplificato
Possiamo ricondurci ad una versione semplificata che **comunque cattura tutti gli aspetti dello schema generale**.


## Compito del controllista

Il nostro ruolo è quello di progettare un **regolatore** e fare in modo che la $y$ sia il più simile possibile a $w$.

Dobbiamo stare attenti ai disturbi sull'uscita e sulla misura, e dobbiamo cercare di attenuarli il più possibile.

## Disaccoppiamento frequenziale dei segnali

Facciamo un'ipotesi per operare meglio sui sistemi da controllare:
**Supponiamo** che nelle nostre applicazioni (e in generale in ambito ingegneristico) tipicamente le bande dei segnali in ingresso $w(t)$, $d(t)$ e $n(t)$ siano limitate in alcuni range.

- $w(t)$ e $d(t)$ hanno bande a **basse frequenze**
- $n(t)$ ha bande ad **alte frequenze**

Ipotizziamo che quindi esista una certa **separazione frequenziale** tra questi segnali.

> [!question] Ma w non può subire una variazione immediata (e quindi avere una trasformata con infiniti valori?)


## Stabilità dei sistemi di controllo


## Prestazioni di un sistema di controllo
- Specifiche (o requisiti) statiche (per $t \to \infty$)
- Specifiche (o requisiti) dinamiche (legate al transitorio)
	Ci interessa in particolare
	- la *sovraelongazione*
	- e il *tempo di assestamento*

### Prestazioni dinamiche

- **Tempo di assestamento**, **sovraelongazione massimi** in risposta ad un riferimento $w$
- **Risposta a disturbi** $d$ e $n$.
	Un diagramma di bode che in certe frequenze deve essere molto negativo in ampiezza.
- Moderazione della variabile di controllo $u$, in entrata al sistema vero e proprio

## Stabilità robusta


> [!warning]
> Noi vorremmo la **stabilità della $F(s)$**!!!

*Potremmo* già farlo considerando i poli della $F(s)$, ma proviamo a ragionare **in frequenza:**


> [!warning] Criterio di bode (IMPORTANTE)
> Voglio la stabilità del **sistema retroazionato**
> !!! eppure !!!
> **lo faccio controllando delle proprietà sul sistema in anello aperto $L(s)$**
>
> Mi serve solo **un punto del diagramma di Bode** per determinare se la $L(s)$ rispetta il citerio.

Si dimostra che la **stabilità robusta** è legata **esclusivamente** ai **poli della funzione di trasferimento di $L(s)$**.

## Margine di fase e di ampiezza

*Ci servono per enunciare il criterio di Bode*

> [!tip] Definizione: $\omega_c$
> Pulsazione critica, tc.
> $$|L(\omega_c)=0|_{dB}$$

^d7de59

Ovvero la omega per cui avviene l'intersezione del diagramma di Bode in ampiezza con l'asse dei 0 dB.


> [!tip] Margine di fase
>
> $$
>\begin{aligned}
> M_f &= arg(L(j\omega_c)) - (-180\deg) \\
> &= 180\deg + arg(L(j\omega_c))
>\end{aligned}
> $$
>
> Ovvero la "distanza con segno" rispetto ai -180gradi

^8e11ef

> [!tip] Definizione: $\omega_\pi$
> $$ \omega_\pi $$ per il quale
> $$arg(L(j\omega_\pi))= -180\deg$$

Ovvero il duale della [[#^d7de59|pulsazione critica]].

> [!tip] Margine di ampiezza
> $$M_a = -|L(\omega_\pi)|_{dB}$$

> [!error] Condizione che non ci piace:
> - Ampiezza: 0db
> - Fase: 180deg

## Criterio di Bode (IMPORTANTE)

*Teorema (Criterio di Bode)*

**Ipotesi**:
- $L(s)$ non ha poli a parte reale (strettamente) negativa
- Il diagramma di bode del modulo di $L(j\omega)$ attraversa solo una volta l'asse a $0 \ dB$

**Tesi**:
Il sistema **retroazionato** è **asintoticamente stabile** (stabilità robusta)

SE E SOLO SE

$\mu > 0$ e $M_f > 0$

> [!warning] ATTENZIONE
> Do delle condizioni sulla $L$ per avere risultati della $F$. A me interessa la stabilità del sistema **retroazionato**.

**Osservazioni**:
- Noi calcoliamo il **margine di fase** (non ci basta sia maggiore di 0)
- La $L$ non la abbiamo. Useremo questo metodo per **sintesi**.

Ricordiamo che $L(j\omega) = R(j\omega) G(j \omega)$, di cui conosciamo la $G$ ma **possiamo scegliere** la $R$.


### Margini di fase: casi patologici

- **Intersezioni multiple**
- **Nessuna intersezione**

Ci rendono impossibile applicare il criterio di Bode.

### Robustezza rispetto a incertezze sul guadagno

Il margine di guadagno ci dice **quanto possiamo cambiare il guagagno statico** prima che il nostro **sistema in retrazione diventi instabile**.

Ci dice quanto robusto sono *in stabilità* in termini di variazione del guadagno.

### Robustezza rispetto a ritardi temporali

Supponiamo di avere un sistema in cui supponiamo di non avere ritardi, ma alla fine ci ritroviamo un ritardo.

Se andiamo a calcolare l'argomento della $L$ finale, ovvero quella con il ritardo, ci accorgiamo che il ritardo **riduce** il margine di fase.

Quindi il **margine di fase** è un **indice di robustezza rispetto ad eventuali ritardi**

$$
\tau_{\max} < \frac{M_f}{\omega_c}
$$

*Ripassare BIBO stabile, stabilità asintotica*


## Funzioni di sensitività

Non abbiamo solo l'ingresso la $w$, ma abbiamo altri input ($n$, $d$).
$$w = y_{RIF}$$
Dovrei cercare di capire cosa accade quando agiscono tutti e tre gli ingressi.

Possiamo sfruttare una proprietà legata alla **linearità** del sistema, ovvero la **sovrapposizione degli effetti**.

Oltre ad essere interessati all'uscita, siamo anche interessati a:
- $e(t) = w(t) - y(t)$;
- $u(t)$ è **l'ingresso di controllo del sistema**, ovvero quello in uscita al controllore $R(s)$.

Abbiamo quindi un sistema con **tre ingressi e tre uscite**.

*Vedi onenote per spiegazione delle funz.*

> [!tldr] Funzioni di sensitività
> Le funzioni di sensitività sono **funzioni di trasferimento**


Cercheremo di avere: ....


Possiamo quindi rimappare le specifiche che abbiamo visto su queste appena trovate.

**Vogliamo relazionare le funzioni di trasferimento alla $L(j\omega)$**


> [!tip] Ricorda!
> Ho bisogno di proprietà in anello chiuso, ma grazie al **criterio di Bode** posso verificare una condizione su $L$ e non sul sistema retroazionato.

### Separazione di banda

Sarà fondamentale la **separazione di banda** vista in precedenza.
- $w,d$ in **basse frequenze**
- $n$ in **alte frequenza**


Vogliamo quindi una $R$ tale che:
- $|L(jw)| \gg 1$ a basse frequenze
- $|L(jw)| \ll 1$ ad alte frequenze

*Vedi onenote*


## Poli c.c. di $F(s)$ e margine di fase

**Approssimiamo $F(s)$ a poli complessi coniugati dominanti.**

Questo perchè possiamo considerare che **tutto il resto agisce dopo (in frequenza) quindi non ci interessa**

Usiamo due poli c.c. perchè *inglobano* anche il caso di poli reali. Vedremo che infatti il comportamento del sistema è questo.

... *Vedi slide e onenote*

Abbiamo quindi trovato una **relazione** tra **un parametro del sistema in anello chiuso $\xi$** (ha a che fare con la $F(j\omega)$) ed **un parametro ($M_f$) del sistema in anello aperto** (ha a che fare con la $L(j\omega)$)

> [!tldr]  Margine di fase
> **Formula:**
> $$\xi \approx \frac{M_f}{100}$$
>
> **Parametri coinvolti:**
> - tempo di assestamento
> - sovraelongazione

> [!warning] Ricorda
> $$ L(j\omega) = R(j\omega)G(j\omega)$$

## Analisi dell'errore ad un gradino

Ovvero l'errore che commettiamo per $t \to \infty$

*Vedi onenote*


> [!warning] Nota
> n(t) alte frequenze che non ha una componente continua (la sua media è circa 0)
>
> Quindi non aspettiamo che abbia un 1(t).
>
> Inoltre se la F è fatta bene (come vista prima) la n è ridotta di un sacco a basse freq.


## Analisi statica: errore a ingressi $W/s^k$

Generalizzazione del caso precedente

Se $k = 2$: rampa

*Per casa: fare conto che abbiamo fatto*

*Vedi slides*

Se impongo un segnale che ha k poli nell'origine, ho bisogno di almeno $k$ poli nell'origine per non divergere. Se $g = k-1$ allora avrò un errore finito.

Per una rampa ho bisogno di almeno 2 poli nell'origine (per non divergere).

> [!tldr] **Principio del modello interno**
>

#### Qual è il significato di questa condizione?

*Vedi onenote*
