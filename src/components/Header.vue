<template>
  
  <header>

    <div class="h-left">
      <h1><a href=""> boolflix</a></h1>
    </div>

    <div class="h-right">
      <select
      v-model="genere" 
      @change="$emit('selezioneGenere', genere)">
        <option value="" selected>Film e Serie TV</option>
        <option value="film">Film</option>
        <option value="serie">Serie TV</option>
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
@import '~@fontsource/roboto-condensed/700.css';

  header{
    padding: 20px;
    height: 80px;
    background-color: black;
    background-image: linear-gradient(black, rgb(32, 32, 32));
    @include flex-between ;   

    h1{
      font-family: 'Roboto Condensed', sans-serif;
      text-transform: uppercase;
      font-size: 40px;

      a{
        color: red;
        text-decoration: none;
      }
    }

    .h-right{

      select{
        background-color: transparent;
        color: goldenrod;
        border: none;
        padding: 10px;
        border-radius: 30px;
        cursor: pointer;
        margin-right: 30px;

        option{
          background-color: black;
          background-image: linear-gradient(white, black, white);
          border: none;
        }
      }

      input{
        background-color: black;
        border: none;
        border-top-left-radius: 10px;
        border-bottom-left-radius: 10px;
        padding: 5px;
        color: goldenrod;
      }
      input::placeholder{
        color: goldenrod;
      }

      button{
        background-color: goldenrod;
        border: none;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
        padding: 5px;
        margin-left: 1px;
        cursor: pointer;
      }
    }
  }
</style>