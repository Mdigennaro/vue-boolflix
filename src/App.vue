<template>
  <div id="app">

    <Header @cercaFilm="cercaFilm" 
    />


    <Main v-if="movie.length > 0" :listItem="movie"
    section="Film"
    />
    <Main v-if="tv.length > 0" :listItem="tv"
    section="Serie Tv"
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
      movie:[],
      tv:[],

      apiUrl:'https://api.themoviedb.org/3/search/',

      type:'',
      genere: '',
      
      apiParams:{
        api_key: '84bd9ebc42509041ef2d7fe87c3946c6',
        language: 'it-IT',
        query: '',
      },

    }
  },


  methods:{
    getApi(type, tendenza = false){

      let apiUrlGenerato = '';
      if(!tendenza){
        apiUrlGenerato = this.apiUrl+type;
      }else{
        apiUrlGenerato =`https://api.themoviedb.org/3/${type}/popular`
      }

      axios.get(apiUrlGenerato, {params: this.apiParams})
        .then(r =>{
          this[type] = r.data.results;
          console.log('type',this[type]);
        })
        .catch(e =>{
          console.log(e);
        })
    },


    cercaFilm(nomeFilm, genere){
      this.movie = [];
      this.tv = [];

      this.apiParams.query = nomeFilm;
      console.log(nomeFilm);
      if (genere === '') {
        this.getApi('movie');
        this.getApi('tv');
      }else{
        this.getApi(genere);
      }
    },    

       
        
  },

  mounted(){
    this.getApi('movie', true);
    this.getApi('tv', true);
  }
}
</script>

<style lang="scss">
@import './assets/style/generals.scss';
@import '~@fontsource/roboto-condensed/index.css';
  #app{
    min-height: 100vh;
    background-color: black;
    
  }
</style>
