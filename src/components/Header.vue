<template>
  
  <header>

    <div class="h-left">
      <img src="" alt="logo">
    </div>

    <div class="h-right">
      <select
      v-model="genere" 
      @change="$emit('selezioneGenere', genere)">
        <option value="" selected>Film e Serie TV</option>
        <option value="movie">Film</option>
        <option value="tv">Serie TV</option>
      </select>
      <input 
      type="text" 
      placeholder="Ricerca film"
      v-model="nomeFilm"
      @keyup.enter="$emit('cercaFilm', nomeFilm)"
      >
      <button 
      @click="$emit('cercaFilm', nomeFilm)"
      >
      Search
      </button>
    </div>

  </header>

</template>

<script>
export default {
  nome: "Header",

  data(){
    return{
      nomeFilm:'',
      genere:''
    }
  }
}
</script>

<style lang="scss">
@import "../assets/style/mixins.scss" ;
  header{
    padding: 20px;
    height: 80px;
    background-color: black;
    @include flex-between ;   
  }
</style>