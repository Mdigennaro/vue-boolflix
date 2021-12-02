<template>
  <div id="app">
    <Header @cercaFilm="cercaFilm" />
    <Main :menu="listaFilm"
    />
  </div>
</template>

<script>

import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios';


export default {
  name: 'App',
  components: {
    Header,
    Main

  },

  data(){
    return{
      listaFilm:[],

      apiUrl:('https://api.themoviedb.org/3/search/movie'),
      
      apiParams:{
        api_key: '84bd9ebc42509041ef2d7fe87c3946c6',
        language: 'it-IT',
        query: 'ritorno al futuro'
      },

      filmInserito:'',
    }
  },


  methods:{
    getApi(){
      axios.get(this.apiUrl, {params: this.apiParams})
        .then(r =>{
          this.listaFilm = r.data.results;
          console.log(this.listaFilm);

        })
        .catch(e =>{
          console.log(e);
        })
    },

    cercaFilm(nomeFilm){
      this.apiParams.query = nomeFilm;
      console.log(nomeFilm);
      this.getApi();
    },    
  },

  mounted(){
    this.getApi();
  }
}
</script>

<style lang="scss">
@import "./assets/style/generals.scss";

  #app{
    min-height: 100vh;
  }
</style>
