<script>

export default{
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
    <article class="col-3 p-2">
        <div class="card w-100 h-100 p-2">
            <img :src=" cards.card_images[0].image_url" class="card-img-top" alt="...">
            <div class="card-body text-center">
                <p class="card-text ">{{ cards.name }}</p>
                <p class="card-text">{{ cards.archetype }}</p>
            </div>
        </div>
    </article>
</template>

<style scoped>

</style>
