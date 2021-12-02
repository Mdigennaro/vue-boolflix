<template>

  <div class="film">
    <h1>{{film.title}}</h1>
    <h3>{{film.original_title}}</h3>
    <p v-if="film.original_language === 'it' "><img src="../assets/img/it.png" :alt="film.original_language"></p>
    <p v-if="film.original_language === 'en' "><img src="../assets/img/en.png" :alt="film.original_language"></p>
    <p v-if="film.original_language !== 'it' && film.original_language !== 'en' ">{{film.original_language}}</p>
    <p>{{film.vote_average}}</p>
  </div>

</template>

<script>
export default {
  nome: "CompilationFilm",
  props:{
    film: Object
  },

}
</script>

<style lang="scss">
.film{
  text-align: center;
  margin: 20px;
  
  p{
    img{
      width: 20px;
    }
  }
}
</style>