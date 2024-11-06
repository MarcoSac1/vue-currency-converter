<script>
export default{
    components: {
        
    },
    data(){
        return{
            value1:'',
            value2:'',
            fromCurrency: 'EUR',  // Valuta di partenza di default
            toCurrency: 'USD',    // Valuta di destinazione di default
            currencies: []
        }
    },
    props:{
        currencies:{
            type: Array,
            required: true
        }
    }
    
}




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
<!-- v-model="cercato"  -->
<style scoped>
    .dropdown-menu {
        max-height: 500px;
        overflow-y: auto;
    }
</style>
