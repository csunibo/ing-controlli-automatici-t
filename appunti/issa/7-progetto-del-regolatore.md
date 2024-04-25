
> [!warning] Cosa ci interessa?
> Ricordiamo che a noi interessano le specifiche del **sistema in anello chiuso**

> [!tldr] Obiettivo
> $$y(t) \approx w(t) = y_{\text{RIF}}$$

## Riepilogo specifiche

#### Stabilità robusta

Si traduce in una certa $M_f > M_f^*$ da ottenere. Ci possono essere incertezze sui parametri e sui ritardi.

### Precisione statica

- Errore in modulo o 
- errore a regime 

in risposta a segnali *canonici*, ovvero segnali del tipo $1/s^k$. Di solito useremo il gradino


> [!question] Guadagno e poli? Quando uno e quando l'altro? [[#Sintesi del regolatore statico]]

### Precisione dinamica

- **Sovraelongazione**
- **Tempo di assestamento**

### Attenuazione disturbo in uscita

Immaginiamo un $d(t)$ con una certa ampiezza sinusoidale.
Vogliamo che sulla $y_d(t)$ sia attenuata di ....

Specificata sul range di pulsazioni e sull'attenuazione (positiva) in dB.

**Esempio**: Se lo voglio attenuare di 40dB 


### Fisica realizzabilità del regolatore

Possiamo aggiungere dei poli in alta frequenza

# Vincoli sul diagramma di bode della $L$

## Specifiche in termini di guadagno d'anello

### Precisione statica
> [!warning] Nota: 
> Se $L(s)$ ha polo in $s=0 \implies e_\infty = 0$, ma questo introduce uno sfasamento di $-90^\circ$ 


### Precisione dinamica
#### Sovraelongazione $S\%$

*Vedi onenote*

**Bode**: rettangolo nella FASE da non toccare SOLAMENTE ad $\omega_c$.


### Attenuazione disturbo in uscita $d(t)$

Ci interessa solamente in un range di frequenze, ovvero quelle dove esiste $d(t)$ (a basse frequenze)

Se d(t) è una sinusoide, a regime l'uscita è una sinusoide con la stessa fase e ampiezza moltiplicata per il modulo della funz di trasferimento, ovvero $S(s)$

Avremo anche uno sfasamento ma ci interessa solo l'ampiezza

Il modulo della S è l'opposto del modulo della L di omega a basse frequenze, ed è li che agisce la d(t)

**Quindi**
La specifica si traduce in $|L(j\omega)|_{db} >= A_d \ dB$, ovvero **una zona a basse frequenze** in cui la $L(j \omega)$ non deve passare 

**Bode**: rettangolo IN BASSO A SINISTRA


### Attenuazione disturbo di misura $n(t)$

Anche questo **ci interessa solo in un range di frequenze**, ovvero quelle di $n(t)$ (freq. elevate).

Per attenuare la $F$ oltre $\omega_c$ dobbiamo ridurre $|L(j\omega)|_{dB}$. (vedi approssimazione dalle slide).

$$
|L(j\omega)|_{dB} \le -A_n \ dB
$$
con $A_n$ attenuazione che vogliamo raggiungere.

**QUINDI** si traduce in una zona ad alte frequenze in cui la L non deve passare 

**Bode:** rettangolo IN ALTO A DESTRA



### Moderazione variabile di controllo $u(t)$

Ci interessano relativamente.

Sono specifiche sulla $Q(t)$.

In particolare dobbiamo:
- limitare $\omega_c$, perchè prima la $Q$ è controllata solo da $G$
- realizzare $R$ come passa basso

### Fisica realizzabilità del regolatore $R(s)$

> [!warning] Importante
> Il **grado relativo** del regolatore deve essere $\ge 0$.
> 
> Il grado del denominatore di $R(s)$ $\ge$ del grado del denominatore

**Come lo garantiamo?** Aggiungiamo poli in alta frequenza!

# Sintesi del regolatore

## Metodo "loop shaping"

- *loop*: $L(j\omega)$
- *shaping*: dare una certa forma

**Obiettivo**: scegliere **poli** e **zeri** di $R(s)$

Lavoriamo avendo in mente il diagramma di Bode della $L(j\omega)$ risultante.
$$L(j\omega) = R(j\omega)G(j\omega)$$

### Passaggi
Progettiamo R(s) come 
- regolatore statico: soddisfa specifiche statiche
- regolatore dinamico: soddisfa specifiche dinamiche

in serie.

### Regolatore statico

Di solito $|e_\infty| \le e^\star, e_\infty = 0$ in risposta a qualcosa.

Per fare ciò possiamo:
- aumentare il guadagno
- inserire poli nell'origine

**Struttura**:
$$ R_s(s) = \frac{\mu_s}{s^k} $$

**Decidere**
- se aumentare il guadagno
- se e quanti poli mettere nell'origine
### Regolatore dinamico

Di solito aggiungeremo poli / zeri **reali**.


> [!warning] Attenzione
> Posso aggiungere **solo uno dei due tra $\mu_s$ e $\mu_d$** (o lo metto nel regolatore statico o lo metto nel regolatore dinamico).
> 
> Questo perchè i due blocchi sono in serie, quindi la funzione di trasf. del regolatore intero è il prodotto delle due f. di trasf.



### Sintesi del regolatore statico

Aumentando il guadagno **DIMINUISCO MA NON PORTO MAI A ZERO** il mio errore a regime.

Posso altrimenti mettere un **polo nell'origine**.

> [!question] Perchè non mettere sempre un polo nell'origine?
> 
> Perchè mi aggiunge **sempre** uno sfasamento nelle frequenze di $-90^\circ$, che quindi poi è difficile compensare per rispettare il margine di fase.

### Sintesi del regolatore dinamico

**Obiettivi**:
- imporre $\omega_c$ in un certo intervallo
- garantire un dato margine di fase $M_f$
- garantire una certa attenuazione a pulsazioni elevate (specifica $n(t)$, non è troppo difficile) 

Lavoriamo sul **sistema esteso**, ovvero il sistema $R_s$ in serie a $G$.

#### Scenario A

#### Rete ritardatrice

Funzione di trasf. che ha 
- **un polo reale negativo in $-\frac{1}{\tau s}$**
- **uno zero reale negativo in $-\frac{1}{\tau}$**

$$ R_d(s) = \frac{1 + \alpha \tau s}{1 + \tau s} \qquad 0 < \alpha < 1 $$

Valore di regime di attenuazione: $20\log(\alpha) < 0dB$

> [!warning] Attenzione
> La fase della rete è **sempre negativa**.
> 
> In realtà non ci piace, ma bisogna considerarlo. L'effetto che vogliamo è quello di attenuare dopo una certa soglia.
> $$ \omega^\star = \frac{1}{\tau\sqrt{\alpha}}$$
> 
> Voglio fare in modo che nel mio range dove la fase mi importa $[\omega_{c,\min}; \omega_{c,\max}]$ il ritardo sia già rientrato.


#### Tuning approssimato
Lo posso usare se posso abbassare abbastanza dove si trova il polo. Il problema si pone se "sfaccio" quello che ho fatto nell'attenuazione dei disturbi. Altrimenti uso le [[#Formule di inversione]]
#### Formule di inversione

## Scenario B

Non risolvo nulla se cambio la zona di attraversamento.

#### Obiettivo
- Aumentare la fase
- Amplificare **il meno possibile** l'ampiezza

#### Come facciamo?
- Aggiungiamo 1 o più zeri a pulsazioni **prima** di quella di attraversamento
- Aggiungiamo 1 o più poli a pulsazioni **più elevate** per evitare amplificazione e fisica realizzabilità

### Rete ritardatrice

## Regolatore dinamico per lo scenario B


Un'alternativa è riprovare B, ma per semplicità posso anche risolvere la A

# Controllori PID

PID: Proporzionale Integrale Derivativo

### Casi speciali
| Nome | Caratt. |
| ---- | ---- |
| Regolatore P | Proporzionale |
| Regolatore I | Rete ritardatrice con polo nell'origine e zero a $\infty$ |
| Regolare PI | Rete ritardatrice con polo nell'origine e zero in $-1/T_i$ |
| Regolatore PD | Rete anticipatrice con zero in $-1/T_d$ e polo a infinito. |
