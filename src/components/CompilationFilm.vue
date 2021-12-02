<template>

  <div class="film">
    <h1>{{film.title}}</h1>
    <h3>{{film.original_title}}</h3>
    <p>{{film.original_language}}</p>
    <p>{{film.vote_average}}</p>
  </div>

</template>

<script>
export default {
  nome: "CompilationFilm",
  props:{
    film: Object
  },

  data(){
    return{
      bandieraInglese:('../assets/img/en.png'),
      bandieraItalia:('../assets/img/it.png')
    }
  },

  methods:{
    
    aBandiera(){
      if(this.film.original_language === 'en' ){
        this.film.original_language = this.bandieraInglese
      }

      if(this.film.original_language === 'it' ){
        this.film.original_language = this.bandieraItalia
      }
    }
  }
}
</script>

<style>
.film{
  text-align: center;
  margin: 20px;
}
</style>