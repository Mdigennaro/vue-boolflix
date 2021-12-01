<template>
  <div id="app">
    <Header  />
    <Main :menu="listaFilm"/>
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
      apiUrl:('https://api.themoviedb.org/3/search/movie?api_key=84bd9ebc42509041ef2d7fe87c3946c6&query=ritorno+al+futuro&language=it-IT'),

      listaFilm:[]
    }
  },

  methods:{
    getApi(){
      axios.get(this.apiUrl)
        .then(r =>{
          this.listaFilm = r.data.results;
          console.log(this.listaFilm);

        })
        .catch(e =>{
          console.log(e);
        })
    }
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
