<template>
  <div class="serie">

    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img src="img_avatar.png" alt="Poster" style="width:300px;height:300px;">
        </div>
        <div class="flip-card-back">

          <h1>{{serie.name}}</h1>
          <h3>{{serie.original_name}}</h3>
          <p v-if="serie.original_language === 'it' "><img src="../assets/img/it.png" :alt="serie.original_language"></p>
          <p v-if="serie.original_language === 'en' "><img src="../assets/img/en.png" :alt="serie.original_language"></p>
          <p v-if="serie.original_language !== 'it' && serie.original_language !== 'en' ">{{serie.original_language}}</p>
          <p>{{serie.vote_average}}</p>

        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {

  nome: "CompilationSerie",

  props:{
    serie: Object
  }

}
</script>

<style lang="scss">
@import "../assets/style/mixins.scss";


.serie{
  text-align: center;
  margin: 20px;

  .flip-card {
    background-color: transparent;
    width: 300px;
    height: 300px;
    perspective: 1000px; 
  }

  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.6s;
    transform-style: preserve-3d;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  }

  .flip-card:hover .flip-card-inner {
    transform: rotateY(180deg);
  }

  .flip-card-front, .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    @include flex-center;
    flex-direction: column;
  }

  .flip-card-front {
    background-color: #bbb;
    color: black;
  }

  .flip-card-back {
    background-color: #2980b9;
    color: white;
    transform: rotateY(180deg);
  }
  
  p{
    img{
      width: 30px;
      border-radius: 2px;
    }
  }
}
</style>