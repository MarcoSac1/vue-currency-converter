# Vue 3 + Vite

This template should help get you started developing with Vue 3 in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Vue - Official](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (previously Volar) and disable Vetur


Descrizione:

📚 esercizio di oggi: **Vue 3 Currency Converter**
nome repo: **vue-currency-converter**

Stiamo organizzando dei viaggi all’estero e ci farebbe tanto comodo un convertitore di valute molto veloce da usare all’occorrenza.

In una versione di base, abbiamo due input numerici e due select. L’utente può scrivere in entrambi gli input e convertire nelle valute impostate nelle select.
Le valute presenti come options nelle select sono prese dall’API Frankfurter, gratuita e utilizzabile senza API key. Ogni cambiamento in uno degli input chiama l’endpoint relativo alla conversione tra valute.

Per una versione più avanzata possiamo:

- disabilitare currency nella select in relazione all’altra selezionata (evitare conversione su due currency uguali)
- aggiungere un’intestazione sfruttando la classe Intl di JS per la formattazione delle currency

Se neanche la versione avanzata ci basta, possiamo aggiungere un grafico con Apex Charts (o chart.js o vue-chart-js), da customizzare a piacere.

La grafica nell’anteprima è di esempio, potete realizzarla come preferite.

**Milestone 1**
Creare un componente che contenga un campo di input una select.
Questo componente servirà sia per il primo input che per il secondo ricevendo tramite props la lista delle valute.

**Milestone 2**
Effettuare all’avvio dell’applicazione una chiamata all’API (con axios) per popolare le due select con la lista delle valute. La prima select avrà come valore selezionato di default "Euro" e la seconda "United State Dollar".

**Milestone 3**
Ogni volta che l’utente scrive qualcosa in uno dei due input bisognerà fare in modo che venga effettuata una chiamata all’API per ottenere il valore convertito nella valuta selezionata.

**Milestone 4**
Al cambio di un valore selezionato in una delle due select bisognerà effettuare una nuova chiamata all'API per ottenere il nuovo valore convertito nella valuta corretta.
