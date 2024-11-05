<script>
import Card from './Card.vue'

export default{
    components:{
        Card
    },
    data(){
        return{

        }
    },
    props:{
        cards:{
            type: Array,
            required: true
        }
    }
}
</script>

<template>
    <section class="container rounded p-5 mb-4">
        <h1 class=" text-light"> Currency Converter: {{ cards.length }}</h1>
        <div class="col-12 ">
            <div class="row">
                <Card v-for="(cards, index) in cards" :key="index" :cards="cards"/>
            </div>
        </div>
    </section>
</template>

<style scoped>
section.container{
    background-image: linear-gradient( 40deg,  #e4e26d 5%, #ff4b4b 100%);
}
</style>
