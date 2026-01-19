---
title: Lo scandalo di RANDU
description: ""
slug:
date: 2026-01-19
draft: false
tags:
  - numeriPseudoCasuali
  - randu
  - generatoreLineareCongruenziale
  - MonteCarlo
  - correlazioniNumeriche
  - distribuzioneUniforme
  - patternTridimensionali
  - storiaCalcoloScientifico
  - matematicaComputazionale
  - difettiAlgoritmi
categories: []
cover:
  image: copertina.jpg
  relative: true
---
Negli anni ’60, nei laboratori di calcolo scientifico, un piccolo dettaglio algoritmico avrebbe cambiato il modo in cui gli studiosi guardano ai numeri casuali. Quel dettaglio si chiamava **RANDU**, uno dei generatori di numeri pseudocasuali più diffusi… e più problematici della storia.

---
## Che cos’è RANDU?

RANDU è un [generatore lineare congruenziale](https://it.wikipedia.org/wiki/Generatore_lineare_congruenziale), un algoritmo che produce sequenze di numeri apparentemente casuali secondo la formula:

$$X_{n+1} = (a \cdot X_{n} + c) \mod m$$

Nel caso specifico di RANDU, i parametri erano:

- a=65539    
- m= $2^{31}$    
- c= 0

Questo algoritmo era incorporato nei computer IBM e utilizzato in simulazioni [Monte Carlo](https://it.wikipedia.org/wiki/Metodo_Monte_Carlo) in fisica, ingegneria e statistica. Appariva efficiente e “casuale” a prima vista, tanto da guadagnarsi la fiducia di intere generazioni di scienziati.

Effettivamente se proviamo a generare un milione di numeri e facciamo l'istogramma, appare una distribuzione uniforme....

![Distribuzione Numeri RANDU](Istogramma.png)

Ora proviamo a graficare i numeri generati da RANDU separandoli in **triple successive di numeri generati**, cioè le sequenze $(X_n,X_{n+1},X_{n+2})$. 

![Grafico 3D OK](3D_ok.png)

Ancora, la distribuzione in 3 dimensioni appare anch'essa uniforme.....
Invece se proviamo a ruotare leggermente ci si accorge che

![Distribuzione 3D RANDU in fogli](3D_azz.png)

>In uno spazio tridimensionale, i punti non si distribuiscono uniformemente come ci si aspetterebbe da una sequenza casuale, ma cadono su **un numero limitato di piani distinti**.

Questo fenomeno è dovuto a una scelta inadeguata dei parametri: la sequenza sembra casuale guardata singolarmente, ma le correlazioni tra numeri consecutivi introducono pattern regolari.

Il difetto di RANDU ha avuto effetti concreti: simulazioni Monte Carlo che si basavano su di esso potevano fornire risultati **distorti e falsamente coerenti**. In altre parole, la scienza stava interpretando come casuale ciò che in realtà era strutturato e prevedibile.

Questo non è solo un curioso aneddoto storico. È diventato un **caso di studio classico** sull’importanza di verificare la qualità dei generatori di numeri pseudocasuali prima di usarli in applicazioni critiche. Anche oggi, quando si progettano algoritmi per simulazioni, crittografia o intelligenza artificiale, il principio rimane lo stesso: un numero casuale mal progettato può compromettere interi esperimenti.
