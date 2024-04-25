PDF: [[CAT_parte2_2023_10_11.pdf]]
## Se possiamo misurare l'intero stato

Supponiamo $y(t) = x(t)$ *(ovvero di poter misurare l'intero stato)*:

$$
u(t) = \mathcal K(x(t)),
\qquad \mathcal K: \mathbb R^n \longmapsto \mathbb R^m
$$

in generale la $u$ deve dipendere dall'*errore*, ovvero dalla distanza dello stato attuale dall'equilibrio.

### Sistema LTI ad anello chiuso

Poiché i sistemi che consideriamo sono *lineari*, prendo una $u$ **funzione lineare dello stato**.

$$
u(t) = K \cdot x(t),
\qquad K \in \mathbb R^{m\times n}
$$

*Se faccio questa scelta cosa succede ad $A$?*

Per linearità posso riscrivere
$$
\dot x(t) = A \cdot x(t) + B \cdot K \cdot x(t) \\
= (A+BK) \cdot x(t) \\
= A_{CL} \cdot x(t)
$$

Ottengo un **sistema ad anello chiuso**, con $A_{CL} = A + BK$ *(CL sta per "closed loop")*, in cui posso scegliere $K$, tali che:

> **TUTTI GLI AUTOVALORI DELLA MATRICE $A_{CL}$ ABBIANO PARTE REALE NEGATIVA**


> [!info] Nota: equilibri non in 0
> Se $x_e$ equilibrio con $u_e$, *vedi onenote*

Si può far vedere che questo obiettivo (nello *spazio di stato*) si può raggiungere solo in determinati fattori del sistema, in particolare dalla coppia $(A,B)$ ed è legata alla proprietà di **raggiungibilità**.

> [!tip] Proprietà strutturali
>  - di **raggiungibilità**: cambiando il mio ingresso posso raggiungere tutti i punti dello spazio di stato
>  - di **controllabilità**


Se c'è **raggiungibilità** si possono *allocare* tutti gli autovalori dove si vuole *(non lo faremo in questo corso)*.

## Se non è possibile misurare l'intero stato
$$
y(t) \ne x(t)
$$

Posso:
- **ricostruire lo stato** (progetto una copia del mio sistema per ricostruirmi lo stato): proprietà di **osservabilità** e **rivelabilità**; dipende dalla coppia $(A,C)$. $$ u(t) = K \hat x(t) \qquad \hat x: \text{stato ricostruito}$$

Next: [[2.3 - Linearizzazione]]
