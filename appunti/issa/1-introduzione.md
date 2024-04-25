PDF: [[CAT_parte1_2023_09_18.pdf]]

**Sistema automatico** basato su *leggi matematiche* e *algoritmi.*

## Notazione ed elementi costitutivi

### Sistema
**Sistema** per il quale vogliamo ottenere il *comportamento automatico*
#### Ingressi
Un sistema può essere regolato / attuato, ovvero attraverso delle variabili di **ingresso**.

Devono esservi sempre delle variabili di ingresso.
#### Uscite
Un sistema ha delle **uscite**, ovvero dei valori che possiamo utilizzare per "controllare" il sistema.
#### Disturbo (ingressi di disturbo)
Il **disturbo** è un ingresso a tutti gli effetti, ma **non sono controllati da noi**.
#### Obiettivo
Fare in modo che l'uscita sia **il più possibile** simile ad un **==uscita di riferimento==**.


#### Esempio

Sistema: automobile

- Ingresso: acceleratore
- Uscita: velocità del veicolo
- Disturbi: ad esempio attrito aerodinamico o attrito con strada

Riferimento (uscita desiderata): velocità costante desiderata (ad es. impostata dall'utente)

Il sistema deve essere "**controllabile**".

# Controllo in anello aperto e anello chiuso

## Controllo in anello aperto ("feedforward")

E' poco utilizzata, ma comunque viene utilizzata per dare dei "riferimenti nominali".

Se ho un modello ideale, potrei usare solamente l'ingresso e il modello per ottenere l'uscita che desidero

## Controllo in anello chiusto ("feedback" o retroazione)

>[!warning] IMPORTANTE
>Il **controllo in retroazione** è un paradigma centrale nei controlli automatici.



# Progetto di un sistema di controllo

1. Definizione delle specifiche
	
	Qual è il comportamento desiderato del mio sistema? 
	
	Quali sono i parametri con cui voglio arrivare allo stato desiderato?
	- Sovraelongazioni
	- Tempo di assestamento

2. Modellazione del sistema
	Di solito gestita dallo specialista del campo. Si modella con equazioni matematiche.

3. Analisi del sistema
4. Sintesi legge di controllo
5. Simulazione sistema controllato
	Faccio test su modello, test su modelli più realistici
6. Scelta elementi tecnologici
	
7. Sperimentazione