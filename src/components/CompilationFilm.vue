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
  }
}
</script>

<style>
.film{
  text-align: center;
  margin: 20px;
}
</style>