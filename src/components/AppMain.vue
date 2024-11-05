<script>
import AppSearch from './AppSearch.vue';
import CardList from './CardList.vue';
import axios from 'axios';
export default{
    components: {
        CardList,
        AppSearch
    },
    data(){
        return{
            cards:[],
            currencies: []
        }
    },
    methods:{

        getConvertion(from, to, amount) {
        axios.get(`https://api.frankfurter.app/latest?base=${from}&symbols=${to}`)
        .then((resp) => resp.json())
        .then((data) => {
        const convertedAmount = (amount * data.rates[to]).toFixed(2);
        alert(`${amount} ${from} = ${convertedAmount} ${to}`);
        });
    },
        getCurrency(){
            axios.get('https://api.frankfurter.app/currencies')
            .then((response) => {
                console.log(response.data);
                this.currencies=response.data;
                console.log(this.currencies);
            })
            .catch(function(error){
                console.log(error);
            })
            .finally(function () {
                
            });
        },

    },
    created(){
        this.getConvertion();
        this.getCurrency();
    }

}
</script>

<template>
    <main>
        <AppSearch @selected='getConvertion':currencies="currencies"/>
        <CardList :cards="cards"/>
    </main>
</template>

<style scoped>

</style>
