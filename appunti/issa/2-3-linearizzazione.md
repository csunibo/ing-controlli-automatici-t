PDF: [[CAT_parte2_2023_10_11.pdf]]

# Linearizzare un sistema non lineare (tempo invariante)

Supponiamo di voler analizzare un sistema

- **NON** lineare
- tempo **invariante**

**vicino ad un equilibrio**.

Sia $(x_e, u_e)$ una **coppia di equilibrio**, ($f(x_e, u_e)=0$), utilizziamo lo sviluppo in serie di Taylor fino al primo termine.

> **Analogia:**
> Approssimazione lineare di una funzione

Modelleremo come LTI l'**errore relativo ad uno stato di equilibrio**.

> **Perchè prendo un punto di equilibrio?**
>
> *In generale posso farla su una generica traiettoria, ma se lo faccio su una coppia di equilibrio ottengo un sistema **tempo invariante**.*

## Come si linearizza?

Considero una traiettoria del sistema, a partire dall'equilibrio $(x_e, u_e)$.

Scriviamo lo stato $x(t)$ come:
$$x(t) = x_e + \tilde x(t)$$
con:

- $x_e$: stato di equilibrio
- $\tilde x(t)$: variazione rispetto all'equilibrio

Scriviamo l'ingresso $u(t)$ come:
$$u(t) = u_e + \tilde u(t)$$
con:

- $u_e$: ingresso di equilibrio
- $\tilde u(t)$: variazione rispetto all'equilibrio

Essendo una traiettoria, vale che

$$
\frac d{dt} x(t) = \frac d{dt}(\overbrace{x_e + \tilde x(t)}^{x(t)}) =
f(\overbrace{x_e+\tilde x(t)}^{x(t)}, \overbrace{u_e + \tilde u(t)}^{u(t)})
$$

Possiamo però anche esprimere $f(x_e + \tilde x(t), u_e + \tilde u(t))$ come serie di Taylor:

$$
f(x_e + \tilde x(t), u_e + \tilde u(t)) =
\overbrace{f(x_e, u_e)}^{0 \ \text{per definizione}}
- \left.{\frac \partial {\partial x} f(x,u)}\right|_{\substack{x=x_e \\ u=u_e}} (x_e + \tilde x(t) - x_e) \\
- \left.{\frac \partial {\partial u} f(x,u)}\right|_{\substack{x=x_e \\ u=u_e}} (u_e + \tilde u(t) - u_e) \\
- \text{term. di ord. sup.}
$$

Ricordando che la $x_e$ è costante, sappiamo che la derivata di $x_e + \tilde x(t)$ è uguale alla semplice derivata di $\tilde x(t)$:

$$
\frac d {dt}(x_e+\tilde x(t)) = \frac d {dt} \tilde x(t) = \dot{\tilde{x}}(t)
$$
Unendo le due equazioni precedenti otteniamo che
$$
\dot{\tilde{x}} = \text{sviluppo di taylor} + \text{termine di ordine superiore}
$$

Ricordando che $f(x_e, u_e) = 0$ per definizione:
$$
\dot{\tilde{x}}(t)
= \left.{\frac \partial {\partial x} f(x,u)}\right|_{\substack{x=x_e \\ u=u_e}} \tilde x(t) \ +\  \left.{\frac \partial {\partial u} f(x,u)}\right|_{\substack{x=x_e \\ u=u_e}}\tilde{u}(t) +  \text{term. di ord. sup.}
$$

Chiamiamo
$$
A := \left.{\frac{\partial}{\partial{x}}f(x,u)}\right|_{\substack{x=x_e \\ u=u_e}}
=
\left.\begin{bmatrix}
 \frac{\partial{f_1(x,u)}}{\partial{x_1}}
 &\dots
 &\frac{\partial{f_1(x,u)}}{\partial{x_n}}
 \\
 \vdots & \ddots & \vdots
 \\
 \frac{\partial{f_n(x,u)}}{\partial{x_1}}
 &\dots
 &\frac{\partial{f_n(x,u)}}{\partial{x_n}}
\end{bmatrix}
\right|_{\substack{x=x_e \\ u=u_e}}
$$
$$
B := \left.{\frac{\partial}{\partial{u}}f(x,u)}\right|_{\substack{x=x_e \\ u=u_e}}
=
\left.\begin{bmatrix}
 \frac{\partial{f_1(x,u)}}{\partial{u_1}}
 &\dots
 &\frac{\partial{f_1(x,u)}}{\partial{u_n}}
 \\
 \vdots & \ddots & \vdots
 \\
 \frac{\partial{f_n(x,u)}}{\partial{u_1}}
 &\dots
 &\frac{\partial{f_n(x,u)}}{\partial{u_n}}
\end{bmatrix}
\right|_{\substack{x=x_e \\ u=u_e}}
$$

Da cui (ripetendo gli stessi passaggi per $y$)
$$
\dot{\tilde{x}} = A\tilde{x}(t)+B\tilde{u}(t) + \text{term. ordine sup.} \\
\tilde{y} = C\tilde{x}(t)+D\tilde{u}(t) + \text{term. ordine sup.}
$$

Se voglio *buttare via il resto* allora ci metto un circa uguale

$$
\begin{aligned}
\frac d{dt} \tilde x(t)
 &= A\tilde x(t) + B \tilde u(t) + \text{term. ordine sup.}  \\
 &\approx A \tilde x(t) + B \tilde u(t) \\
\frac d{dt} \tilde y(t)
 &= C \tilde x(t) + D \tilde u(t) + \text{term. ordine sup.}  \\
 &\approx A \tilde x(t) + B \tilde u(t)
\end{aligned}
$$

### Sistema linearizzato

$$
\dot{\Delta{x}}(t) = A \Delta x(t) + B \Delta u(t) \\
\Delta y(t) = C \Delta x(t) + D \Delta u(t)
$$

$\Delta x$ e $\Delta u$ sono le approssimazioni delle variazioni.

## Stabilità e linearizzazione

#### Teorema: stabilità asintotica di linearizzazioni

Dato un sistema **non lineare tempo invariante**
$$\dot x(t) = f (x(t), u(t))$$

**Ipotesi**

- $(x_e, u_e)$ è una coppia di equilibrio;
- il sistema linearizzato intorno ad $(x_e, u_e)$ è **==asintoticamente stabile==**

**Tesi**
L’equilibrio $(x_e, u_e)$, è (localmente) **asintoticamente stabile** nel sistema di partenza.

*Source: [[CAT_parte2_2023_10_11.pdf#page=103&selection=4,0,53,39|CAT_parte2_2023_10_11, page 103]]*

#### Teorema: instabilità delle linearizzazioni

Dato un sistema non lineare tempo invariante:$$\dot x(t) = f (x(t), u(t))$$

**Ipotesi**

- $(x_e, u_e)$ è una coppia di equilibrio.
- il sistema linearizzato intorno ad $(x_e, u_e)$ ha **==almeno un autovalore a parte reale positiva==**

**Tesi**
L’equilibrio $(x_e,u_e)$ è **instabile**

*Source: [[CAT_parte2_2023_10_11.pdf#page=103&selection=55,0,103,11|CAT_parte2_2023_10_11, page 103]]*

---
> **Nota:**
> Non si può dire nulla in caso si abbiano autovalori  con $\Re(\lambda) \le 0$ ma di cui almeno uno ha $\Re(\lambda) = 0$
>
> > **Analogia con funzione scalare:**
> > Se ho una derivata di una funzione = 0 non ho idea se la funzione cresce o decresce.
> >
> > Se ho un autovalore nullo mi sta dicendo che la linearizzazione non ha informazioni su come varia la funzione di stato.

## Controllo non-lineare mediante linearizzazione

Consideriamo un sistema nonlineare generico:
$$
\dot{x}(t) = f(x(t),u(t))
$$
e la sua linearizzazione intorno all'equilibrio $(x_e, u_e)$
$$
\dot{\Delta{x}}(t) = A_e\Delta{x}(t)+B_e\Delta{u}(t)
$$
Se $\Delta{x} \to 0$, allora $x(t)\to x_e$  (ricordiamo che $x(t)\approx x_e + \Delta{x}$).

Scelgo quindi una $\Delta{u}(t)$ che sia funzione dello stato, ovvero
$$\Delta{u}(t) = K\Delta{x}(t) + \Delta v(t)$$
*con $\Delta{v}(t)$ un termine che mi riservo per eventuali altre correzioni*

Ottengo quindi un sistema ad anello chiuso del tipo
$$
\dot{\Delta{x}}(t) = (A_e + B_e K)\Delta x(t) + B_e \Delta v(t)
$$

Progetto $K$ in modo che la matrice della dinamica ($A_e + B_e K$) sia
asintoticamente stabile.

Grazie ai teoremi visti in precedenza, anche nel sistema non lineare in anello chiuso otterrò un equilibrio (localmente) asintoticamente stabile

### Legge di controllo finale

$$
u(t) = u_e + K \cdot \overbrace{(x(t) - x_e)}^{\approx \Delta x} + \tilde v(t) \\
\approx u_e + K \cdot \Delta x(t) + \tilde v(t)
$$
