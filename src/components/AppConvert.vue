<script>
export default {
    data() {
        return {
            value1: '',
            value2: '',
            fromCurrency: 'EUR',
            toCurrency: 'USD',
            currencies: [],
        };
    },

    watch: {
        fromCurrency: 'updateConversion',
        toCurrency: 'updateConversion',
        value1: 'updateConversion',
    },

    methods: {
        async fetchCurrencies() {
            try {
                const res = await fetch('https://api.frankfurter.app/currencies');
                const data = await res.json();
                this.currencies = Object.keys(data); 
            } catch (error) {
                console.error('Errore nel recupero delle valute:', error);
            }
        },

        async updateConversion() {
            // Pulisce il valore di value2 se value1 è vuoto
            if (!this.value1) {
                this.value2 = '';
                return;
            }
            
            if (this.fromCurrency && this.toCurrency) {
                try {
                    const res = await fetch(`https://api.frankfurter.app/latest?base=${this.fromCurrency}&symbols=${this.toCurrency}`);
                    const data = await res.json();
                    this.value2 = (this.value1 * data.rates[this.toCurrency]).toFixed(2);
                } catch (error) {
                    console.error('Errore nella conversione:', error);
                }
            }
        },
    },

    mounted() {
        this.fetchCurrencies(); 
        this.updateConversion(); 
    },
};
</script>


<template>
    <div class="row">
        <section class="container col-6">
            <div class="input-group m-4">
                <input type="number" v-model="value1" @input="updateConversion" class="form-control col-6" aria-label="Text input with dropdown button">
                <button class="btn btn-danger dropdown-toggle col-4" type="button" data-bs-toggle="dropdown" aria-expanded="false">{{ fromCurrency }}</button>
                <ul class="dropdown-menu dropdown-menu-end">
                    <li v-for="(currency, index) in currencies" :key="index">
                        <a class="dropdown-item" @click="fromCurrency = currency">{{ currency }}</a>
                    </li>
                </ul>
            </div>
            <div class="input-group m-4">
                <input type="number" v-model="value2" class="form-control col-6" aria-label="Text input with dropdown button">
                <button class="btn btn-danger dropdown-toggle col-4" type="button" data-bs-toggle="dropdown" aria-expanded="false">{{ toCurrency }}</button>
                <ul class="dropdown-menu dropdown-menu-end">
                    <li v-for="(currency, index) in currencies" :key="index">
                        <a class="dropdown-item" @click="toCurrency = currency">{{ currency }}</a>
                    </li>
                </ul>
            </div>
            <div class="m-4">
                <p id="first-value">
                    {{ value1 }} {{ fromCurrency }} corrisponde a: 
                </p>
                <h1 class="second-value">
                    {{ value2 }} {{ toCurrency }}
                </h1>
            </div>
        </section>
    </div>
</template>

<style scoped>
    .dropdown-menu {
        max-height: 500px;
        overflow-y: auto;
    }
</style>
