## Introduzione alla funzione di trasferimento

Applicando la trasformata di Laplace è facile ricavare la $X(s)$. Si puù poi applicare l'anti trasformata per ritrovare nel tempo $x(t)$.

## Funzione di trasferimento
Consideriamo adesso **solamente l'evoluzione forzata dell'uscita** (quindi un sistema con stato iniziale *a riposo*).

Cosa succede al variare dell'ingresso $U(s)$ all'uscita?

Chiamiamo tutto ciò che è moltiplicato per $U(s)$ come **funzione di trasferimento**.
$$
G(s) = C(sI - A)^{-1} B +D
$$
**Nel caso SISO** è una funzione scalare, altrimenti vettoriale.

L'uscita *forzata* risulta quindi:

$$
Y_f(s) = G(s) \ U(s)
$$
Ma supponendo che $x(0) = 0$ (ovvero evoluzione libera nulla) avremo che anche l'uscita totale è pari a:
$$
Y(s) = G(s) \ U(s)
$$
In questo caso possiamo scrivere anche che
$$
G(s) = \frac{Y(s)}{U(s)}
$$
*Vedi onenote per grafico funz di trasf.*

**La funzione di trasferimento è quindi una descrizione del rapporto tra input e output del sistema.**

### Come è fatta la $G(s)$?

$$
G(s) = C(sI - A)^{-1}B+D
$$

L'unica parte che dipende da $s$ è la parentesi, ovvero $(sI - A)^{-1}$. 
Andiamo a capire com'è fatta sta matrice.

##### Condizione di esistenza della matrice $(sI-A)^{-1}$
$s \notin \text{autovalori di A}$, altrimenti il $\det{(sI-A)} = 0$ (che è proprio il polinomio caratt. di $A$) e quindi $(sI-A)$ non invertibile.

*Vedi onenote per più passaggi*



### Funzioni di trasferimento di sistemi propri e strettamente propri

Se la $D$ non c'è (il sistema è [[2.0 - Sistemi dinamici in forma di stato#Sistemi **strettamente propri**|strettamente proprio]]) avremo una G con numeratore $n-1$, **strettamente minore** del grado del denominatore di grado $n$.

Se la $D$ c'è (il sistema è **proprio**, ovvero c'è una relazione algebrica diretta tra ingresso e uscita) avremo una G con numeratore e denominatore di grado $n$

> [!warning]
> Stiamo considerando segnali **causali**

- Esempio **derivatore**: NON causale
- Esempio **integratore**: causale
## Funzione di trasferimento pag 16

I **poli** e gli **zeri** sono **reali o complessi coniugati** (poiché radici di polinomi a coefficienti reali).

#### Poli della funzione di trasferimento
I poli della funzione di trasferimento sono **alcuni (o eventualmente tutti) gli autovalori di $A$**.

$$
(sI-A)^{-1} = \frac{\text{adj}(sI-A)}{\det(sI-A)}
$$
### Forme fattorizzate

2 forme fattorizzate
- Forma 1 (*boh non so come si chiama*)
- Forma di Bode

### Relazione con delta di Dirac

Possiamo interpretare la $G(s)$ come la trasformata della risposta a $\delta(t)$.
Infatti
$$
Y(s) = G(s) \cdot U(s)
$$
Pongo $U(s) = 1$ (e quindi $u(t) = \delta(t)$):
$$
Y(s) = G(s)
$$

### Cancellazioni provenendo dalla forma di stato

In generale indicano **mancanza di proprietà strutturali**.

### Relazione tra poli e autovalori di A

I poli sono gli **autovalori della matrice A**.

Se ci sono autovalori che non sono poli questo è legato a 
- non osservabilità oppure
- non controllabilità
### Esempi di cancellazioni

Se ci sono delle cancellazioni nella creazione della $G(s)$.

Esercizio: Fare l'esempio 1 ma prendere $y = x_1$.
## Contenuto informativo della funzione di trasferimento

Se il sistema è **raggiungibile** ed **osservabile** (quindi non ci sono cancellazioni nella f. di trasferimento) allora la **funzione di trasferimento ha lo stesso contenuto informativo delle equazioni di stato e di uscita**.

Si dimostra che la funzione di trasferimento individua la parte dello spazio di stato raggiungibile e osservabile.
## Antitrasformata

Se consideriamo $x(0) = 0$ (risposta forzata)
$$
Y(s) = G(s) U(s)
$$
Se mandiamo una delta di Dirac $u(t) = \delta(t)$ (la cui trasformata $U(s) = 1$) si ha che 
$$ Y(s) = G(s) $$

> Quindi per la risposta all’impulso le radici di $D(s)$ sono i poli di $G(s)$.

[[CAT_parte3_2023_10_16.pdf#page=26&selection=59,0,72,1|CAT_parte3_2023_10_16, page 26]]

Con un delta in ingresso ottengo quindi in uscita l'antitrasformata della funzione $G(s)$.

> [!question] Cos'è la risposta ad un gradino?
> La risposta della funzione quando viene messo come ingresso $1(t)$

## Sviluppo di Heaviside

### Poli singoli

**Esercizio**: rifare la somma (fratti semplici) e controllare che i poli siano gli stessi


> [!info] Residui associati ai poli
> $$
> k_i = \left. (s+p_i) \frac{N(s)}{D(s)} \right|_{s=-p_i}
> $$

*Vedi onenote per spiegazione di come ci siamo arrivati*

#### Poli complessi coniugati
$p_{i,1} = \sigma + j\omega$ 
$p_{i,2} = \sigma - j \omega$


Si fa vedere che anche i **residui associati** sono **complessi coniugati**.

$$
k_{i,1} = Me^{-j\phi} \qquad
k_{i,2} = Me^{j\phi}
$$

....

L'antitrasformata della somma dei due termini associati è

$$
= 2 Me^{-\sigma t}\cos(\omega t + \phi) \cdot 1(t)
$$


### Poli multipli

Pagina 32

Una coppia di poli complessi coniugati mi da un contributo del tipo

*Vedi slides*

### Coppia di poli immaginari puri

> [!error] Attenzione!
> 
> $$
> [2M_{1,1} cos(\omega_n t  + \phi)
> + 2 M_{1,2} t cos(\omega_n t + \phi)] \cdot 1(t)
> $$
> 
> Diverge!!!

## Modi naturali come risposta all'impulso
Lo sviluppo di Heaviside mi dice che posso scrivere $Y(s)$ come una sommatoria di fratti.

Facendo l'antitrasformata di questi fratti, ottengo una combinazione lineare dei cosiddetti **modi naturali** del sistema.

> [!question] Vale solo perchè consideriamo il delta di dirac e quindi G(s) = Y(s)?


## Risposte ad un ingresso generico (pag 36)

In $s$ possiamo scrivere la $Y(s)$ come la somma di un'evoluzione **libera** e di un'**evoluzione forzata**.

Possiamo anche chiamare $Y(s)$ come
$$
Y(s) = \frac{N_l(s)}{D(s)} x(0) + \frac{N_g(s)}{D(s)} \cdot \frac{N_u(s)}{D_u(s)}
$$

Nella $G(s)$ ho una serie di poli, che nello sviluppo di Heaviside mi portano a tanti  fratti sommati. Nella $U(s)$ ho anche qui tanti fratti sommati. Quindi posso considerare la $y(t)$ come la somma di *vedi slides*


Nella mia uscita ho modi naturali che possono venire:
- o dal sistema, ovvero dalla $G(s)$
- oppure dall'ingresso, ovvero dalla $U(s)$

> [!question] Da rispiegare tutta sta storia di "modi naturali come risposta all'impulso" e "risposta ad un ingresso generico" e "divisione della parte relativa ai modi naturali e quella relativa ai modi presenti nell'ingresso"
## Risposte di sistemi elementari
Nel caso di **poli distinti**, per $x(0) = 0$ (risposta forzata)

$$
Y(s) = G(s) U(s) = \sum_i \frac{k_i}{s+p_i} + \sum_i\frac{a_is + b_i}{s^2 + 2\xi_i\omega_{n,i}s+\omega_{n,i}^2}
$$
## Stabilità esterna o BIBO

Si dimostra che questa condizione è equivalente al fatto che **tutti i poli di G(s) siano a parte reale STRETTAMENTE negativa**

E' equivalente alla **stabilità asintotica del sistema** (se non ci sono cancellazioni).

Se con un ingresso limitato faccio divergere l'uscita allora non è più BIBO stabile.

> [!question] Auto-question?
> Sappiamo alcuni sistemi NON BIBO?

[[L4 - Sistemi notevoli]]