<script>
import AppConvert from './AppConvert.vue';
import axios from 'axios';
export default{
    components: {
        AppConvert
    },
    data(){
        return{
            cards:[],
            currencies: []
        }
    },
    
    methods:{


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
        this.getCurrency();
    }

}
</script>

<template>
    <main>
        <AppConvert :currencies="currencies"/>
    </main>
</template>

<style scoped>

</style>
