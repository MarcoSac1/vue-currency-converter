<script>
import AppMain from './components/AppMain.vue';
import AppHeader from './components/AppHeader.vue';

    export default{
      components:{
        AppHeader,
        AppMain
      },
      data(){
        return{

        }
      }
    }
</script>

<template>
  <AppHeader/>
  <AppMain/>
</template>

<style lang="scss">
@use'../node_modules/bootstrap/scss/bootstrap.scss';
@use'./styles/partials/variable' as *;
@use'./styles/partials/mixins' as *;
@use'./styles/general.scss';
</style>
