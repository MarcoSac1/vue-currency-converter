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
        archetypes:{
            type: Array,
            required: true
        }
    }
    
}
</script>

<template >
    <section class="container">
        <div class="dropdown  ">
            <button class="btn btn-danger m-4 dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false" >
                Archetypes selector
            </button>
            <ul class="dropdown-menu dropdown-menu-dark">
                <li  v-for="(archetypes, index) in archetypes" :key="index" :archetypes="archetypes"  >
                    <a class="dropdown-item " @click="$emit('selected', archetypes.archetype_name)"  href="#">{{ archetypes.archetype_name }}</a>
                </li>
            </ul>
        </div>
    </section>
</template>
<!-- v-model="cercato"  -->
<style scoped>
    .dropdown-menu {
        max-height: 500px;
        overflow-y: auto;
    }
</style>
