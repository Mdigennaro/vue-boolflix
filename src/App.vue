<template>
  <div id="app">
    <Header @cercaFilm="cercaFilm" 
    @selezioneGenere="selezioneGenere"
    />
    <Main :menuFilm="listaFilm"
    :menuSerie="listaSerie"
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
      listaSerie:[],

      apiUrlFilm:('https://api.themoviedb.org/3/search/movie'),
      apiUrlSerie:('https://api.themoviedb.org/3/search/tv'),

      type:'',
      
      apiParams:{
        api_key: '84bd9ebc42509041ef2d7fe87c3946c6',
        language: 'it-IT',
        query: 'ritorno al futuro',
      },

      filmInserito:'',
    }
  },


  methods:{
    getApiFilm(){
      axios.get(this.apiUrlFilm, {params: this.apiParams})
        .then(r =>{
          this.listaFilm = r.data.results;
          console.log('film',this.listaFilm);
        })
        .catch(e =>{
          console.log(e);
        })
    },

    getApiSerie(){
      axios.get(this.apiUrlSerie, {params: this.apiParams})
        .then(r =>{
          this.listaSerie = r.data.results;
          console.log('serie',this.listaSerie);

        })
        .catch(e =>{
          console.log(e);
        })
    },

    cercaFilm(nomeFilm){
      this.apiParams.query = nomeFilm;
      console.log(nomeFilm);
      this.getApiFilm();
      this.getApiSerie();
    },    

    selezioneGenere(genere){
      this.type = genere;
      console.log(genere);
    },    
        
  },

  mounted(){
    this.getApiFilm();
    this.getApiSerie();
  }
}
</script>

<style lang="scss">
@import "./assets/style/generals.scss";

  #app{
    min-height: 100vh;
  }
</style>
