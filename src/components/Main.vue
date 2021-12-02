<template>
  <main>

    <Compilation 
    v-for="film in menu" 
    :key="film.id" 
    :film="film"
    />

  </main>
</template>

<script>
import Compilation from './CompilationFilm.vue';

export default {
  nome: "Main",
  
  props:{
    menu: Array,
  },
  components:{
    Compilation
  },


}


</script>

<style lang="scss">
@import "../assets/style/mixins.scss";
main{
  min-height: calc(100vh - 80px) ;
  background-color: gray;
  @include flex-center;

}
</style>