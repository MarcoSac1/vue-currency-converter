<script>
export default{
    components: {
        
    },
    data(){
        return{
            cercato:'',
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

<template >
    <div class="row">
        <section class="container col-6">
            <div class="input-group m-4">
                <input type="number" class="form-control col-6" aria-label="Text input with dropdown button">
                <button class="btn btn-danger dropdown-toggle col-4" type="button" data-bs-toggle="dropdown" aria-expanded="false">Euro</button>
                <ul class="dropdown-menu dropdown-menu-end">
                    <li  v-for="(currencies, index) in currencies" :key="index" :currencies="currencies"  >
                        <a class="dropdown-item " @click="$emit('selected', currencies.data)"  href="#">{{ currencies }}</a>
                    </li>
                </ul>
            </div>
            <div class="input-group m-4">
                <input type="number" class="form-control col-6" aria-label="Text input with dropdown button">
                <button class="btn btn-danger dropdown-toggle col-4" type="button" data-bs-toggle="dropdown" aria-expanded="false">United State Dollar</button>
                <ul class="dropdown-menu dropdown-menu-end">
                    <li  v-for="(currencies, index) in currencies" :key="index" :currencies="currencies"  >
                        <a class="dropdown-item " @click="$emit('selected', currencies.data)"  href="#">{{ currencies }}</a>
                    </li>
                </ul>
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
