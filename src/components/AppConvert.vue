<script>
export default {
    data() {
        return {
            value1: '',
            value2: '',
            fromCurrency: 'EUR',
            toCurrency: 'USD',
            currencies: {}, // Salva valute come oggetto { codice: nomeCompleto }
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
                this.currencies = data; // Salva le valute con nomi completi
            } catch (error) {
                console.error('Errore nel recupero delle valute:', error);
            }
        },

        async updateConversion() {
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
    <div class="row  mt-4 ">
        <section class="container shadow-lg  justify-content-center align-items-center rounded-2 p-4 col-6">
            <div class="input-group mb-4">
                <input type="number" v-model="value1" @input="updateConversion" class="form-control col-6" aria-label="Text input with dropdown button">
                <button class="btn btn-danger dropdown-toggle col-4" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                    {{ currencies[fromCurrency] || fromCurrency }}
                </button>
                <ul class="dropdown-menu dropdown-menu-end">
                    <li v-for="(currencyName, currencyCode) in currencies" :key="currencyCode">
                        <a class="dropdown-item" @click="fromCurrency = currencyCode">{{ currencyName }}</a>
                    </li>
                </ul>
            </div>
            <div class="input-group mb-4">
                <input type="number" v-model="value2" class="form-control col-
                6" aria-label="Text input with dropdown button" >
                <button class="btn btn-danger dropdown-toggle col-4" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                    {{ currencies[toCurrency] || toCurrency }}
                </button>
                <ul class="dropdown-menu dropdown-menu-end">
                    <li v-for="(currencyName, currencyCode) in currencies" :key="currencyCode">
                        <a class="dropdown-item" @click="toCurrency = currencyCode">{{ currencyName }}</a>
                    </li>
                </ul>
            </div>
            <div class="m-4">
                <p id="first-value">
                    {{ value1 }} {{ currencies && fromCurrency }} equivale a: 
                </p>
                <h2 class="second-value">
                    {{ value2 }} {{ currencies && toCurrency }}
                </h2>
            </div>
        </section>
    </div>
</template>


<style scoped>
    .container{ 
        font-size: 1rem;
        background-color: beige;
    }

    button{
        font-size: .8;
    }
    .dropdown-menu {
        max-height: 500px;
        overflow-y: auto;
    }
</style>
