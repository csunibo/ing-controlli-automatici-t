## Risposta ad un segnale di ingresso sinusoidale
Vogliamo calcolare l'uscita in corrispondenza di un ingresso **sinusoidale**.

Consideriamo $G(s)$ con **poli distinti a parte reale negativa** (BIBO stabile)

> [!warning] IMPORTANTE
> ==Se metto in ingresso una sinusoide ad un sistema BIBO stabile, per $t \gg 0$ avrò in uscita **una sinusoide con pulsazione pari a quella originaria**==

> [!tip] Definizione: Risposta a regime permanente
> La risposta per $t \gg 0$ si chiama **risposta a regime permanente** (o a **transitorio esaurito**)

### Perchè BIBO stabile?
Poiché i poli di G(s) sono a parte reale negativa, i contributi $e^{−p_it}\cdot 1(t)$ sono tutti convergenti a zero. 

**Pertanto $y_1(t) \to 0$ per $t \to \infty$**



## Risposta a segnali periodici sviluppabili in serie di Fourier

Scompongo in serie il segnale sinusoidale, do in ingresso ogni componente e sommo le uscite. Ottengo l'uscita che avrei ottenuto se il segnale fosse stato messo in ingresso tutto quanto insieme.

> [!warning]
> Consideriamo dei segnali periodici **A REGIME**, cioè ci dimentichiamo del fatto che prima di 0 debba essere 0 il segnale per farne la trasformata.

## Risposta a segnali periodici trasformabili secondo Fourier

Anche se il segnale non è periodico, ma possiede trasformata di Fourier,

*rivedere cosa viene in uscita mettendo un ingresso una sinusoide matematicamente*


# Risposta in frequenza

$$
G(s)|_{s=j\omega} \in \mathbb C: \text{risposta in frequenza}
$$
Ci dice **come risponde il nostro sistema ad armoniche diverse** in ingresso.
## Identificazione di sistemi dinamici

In alcuni contesti non è possibile operare in modo *model-based*, ovvero ricavare il modello da qualcos'altro e operare in termini controllistici.

Si può quindi pensare ad un approccio *data-driven*, in cui mando in ingresso una serie di segnali e vedo cosa ottengo in output.

# Diagrammi di Bode

Voglio vedere al variare della frequenza di ingresso come si comporta l'ampiezza e la fase dell'uscita (rispetto a quella di ingresso).

Possiamo esprimere la risposta in frequenza in decibel, quindi $|G(j\omega)|_{dB}$ 

*Vedi slide 14 per risposta in frequenza in guadagno e argomento*

Per l'argomento uso i decibel (scala logaritmica). Per la fase invece lascio cos'.

## Risposta in frequenza in guadagno e argomenti

Utilizzando modulo in decibel e argomento **la funzione trasferimento si trasforma tutta in somme e sottrazioni**, quindi le posso analizzare separatamente in [[#Contributi elementari|contributi elementari]].

> [!warning] Attenzione
> Con la **scala logaritmica** non riesco a rappresentare $\omega=0$, perchè per $\omega \to 0^+$, $\log(\omega) \to -\infty$.
> 
> Non esiste l'origine! (**Non devo rappresentare l'origine!!**)

## Contributi elementari
Ci sono vari contributi elementari:
- Per un guadagno statico
- Per poli / zeri nell'origine. Differiscono per un meno in log e arg.
- Per poli / zeri reali.  Stessa cosa di prima.
- Per poli / zeri complessi coniugati. Stessa cosa di prima.

### Guadagno statico

Se $\mu> 0$, valore in decibel positivo, altrimenti negativo.

Stessa cosa per la fase, quindi al variare di $\omega$ la fase non cambia.

Trasla rigidamente in alto o in basso il resto della funzione, sia in ampiezza che in fase.

### Zeri nell'origine

**Ampiezza**
La pendenza si misura in **dB/decade**.
Per g zeri nell'origine, avrò una pendenza di $20g \ dB/dec$.

**Fase**: $90g\deg$
E' un numero solamente immaginario (la funz di trasf), quindi avrò una fase di 90deg.
Se ho g zeri avrò una rotazione ogni volta di 90deg. 
### Poli nell'origine

Tutto uguale a zeri nell'origine, tranne per un meno davanti all'ampiezza.

**Pendenza**: $-20 g \ dB/dec$
**Fase**: $-90g\deg$

### Zeri reali

> [!tip] Diagrammi asintotici
> Un diagramma che rappresenta l'andamento asintotico per omega molto più piccoli della frequenza di taglio e molto più grandi della frequenza di taglio.
> 
> **Per l'esame**: traccio prima i diagrammi asintotici e poi quelli reali

> [!warning] Quando possiamo usare il  diag asintotico?
> Una decade prima ed una decade dopo la freq. di taglio.

> [!tip] Prendiamo sempre $\omega$ positivo

**Pulsazione di taglio**: $\frac 1 {|\tau|}$

E' legato al valore dello zero, quindi questa si sposta insieme allo spostamento dello zero.

> [!warning] 
> Non arrivo mai a $\omega = 0$ nel diagramma di Bode, in quanto per $\omega = 0$ il log tende a $-\infty$.

#### Ampiezza
Pendenza prima della pulsazione di taglio: 0 dB/dec
Pendenza dopo la pulsazione di taglio: 20dB/dec

> [!tip]
> C'è un discostamento massimo di 3dB tra il diagramma reale e quello asintotico.

#### Fase

**Come facciamo a ottenere un grafico più preciso?**: *Vedi onenote*.

$4.81$ equivale a $2/3$ della decade avanti o indietro. Per noi sarà $\approx 5$.

Se lo zero è reale positivo $\tau < 0$ allora avremo uno sfasamento negativo (grafico ribaltato).
#### Osservazioni
Nel diagramma delle ampiezze noto che fino alla freq. di taglio non ho effetto ($\times 1$) sulla sinusoide in ingresso.

Sulla **fase** invece succede qualcosa anche **prima** di arrivare alla pulsazione di taglio se mi metto nella decade prima e dopo la pulsazione di taglio.

### Polo reale

Lo sfasamento della fase per un polo reale **positivo** è lo stesso di uno zero reale **negativo**

Pendenza = -20g dB/dec dopo la puls di taglio.

Pulsazione di taglio: 1/mod(T)

E' quello che abbiamo chiamato **sistema del primo ordine**. 

Corrisponde anche ad un **filtro passa basso**.

#### Risposta a gradino sistemi 1 ordine
*Vedi onenote per risposta al grafino sistemi 1 ordine*

Il filtro passa basso mi sta tagliando tutte le freq. elevate. Da questo la risposta a gradino

**Infatti se prendo T più grande filtra più frequenze alte.**



## Zeri complessi coniugati

#### Ampiezza
Due osservazioni per $\zeta \to 0$:
- la pulsazione  in cui si ottiene il minimo va ad $\alpha_n$
- il picco va a $-\infty$

#### Fase

Per $\zeta = 0$ , ho una discontinuità tra 0 e **180deg**

*E' come se avessimo due zeri che ognuno da un contributo di 90deg*

Minimo a pulsazione:
$$
\omega_r = \alpha_n  \sqrt{1 - 2\zeta^2}
$$
## Poli complessi coniugati

Come se avessi due poli reali. 

Scendo di 40 db/dec dopo la freq di taglio in ampiezza. Più è piccola $\xi$ più l'amplificazione aumenta un sacco vicino alla freq. di risonanza.

Scendo a -180 in fase. Più è grande $\xi$ più la transizione è *morbida*.

### Picco di risonanza
$$
\omega_r = \omega_n\sqrt{1-2\xi^2}
$$

Valore del picco:
$$
|G_d(j\omega_r)| = \frac{1}{2|\xi| \sqrt{1-\xi^2}} \overbrace{\approx}^{\text{vedi sotto}} \frac {1} {2|\xi|}
$$

> [!tip]
> Spesso confonderemo $\omega_r \approx \omega_n$.
> 
> e confonderemo
> $$
> |G_d(j\omega_r)| \approx \frac 1 {2 |\xi|}
> $$

### Poli complessi coniugati *dominanti*


## Ritardo temporale

## Proprietà bloccante degli zeri

## Proprietà di risonanza

Se lo xi non è zero ma molto piccolo non vado a infinito ma sto amplificando molto il segnale nella pulsazione di risonanza


>[!question] Perchè $\xi$ non può essere 0?
>