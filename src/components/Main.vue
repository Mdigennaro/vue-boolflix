<template>
  <main>
    
    <div class="container-film">

      <CompilationFilm 
      v-for="film in menuFilm" 
      :key="film.id" 
      :film="film"
      />

    </div>

    <div class="container-serie">

      <CompilationSerie 
      v-for="serie in menuSerie" 
      :key="serie.id" 
      :serie="serie"
      />

    </div>

  </main>
</template>

<script>
import CompilationFilm from './CompilationFilm.vue';
import CompilationSerie from './CompilationSerie.vue';

export default {
  nome: "Main",
  
  props:{
    menuFilm: Array,
    menuSerie: Array,
  },
  components:{
    CompilationFilm,
    CompilationSerie
  },


}


</script>

<style lang="scss">
@import "../assets/style/mixins.scss";
main{
  height: calc(100vh - 80px) ;
  background-color: gray;
  
  .container-film, .container-serie{
    width: 100%;
    height:50%;
    @include flex-between;
    overflow: hidden;
    overflow-x: scroll;
    padding: 10px;
  
  }
  
}
</style>