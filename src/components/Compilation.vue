<template>

  <div class="film">

    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img v-if="item.poster_path === null" :src="`https://image.tmdb.org/t/p/w342/${item.backdrop_path}`" :alt="item.title || item.name">
          <img v-else :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`" :alt="item.title || item.name">
        </div>
        <div class="flip-card-back">

          <h2>{{item.title || item.name }}</h2>
          <h4>{{item.original_title || item.original_name}}</h4>
          <p v-if="item.original_language === 'it' "><img src="../assets/img/it.png" :alt="item.original_language"></p>
          <p v-if="item.original_language === 'en' "><img src="../assets/img/en.png" :alt="item.original_language"></p>
          <p v-if="item.original_language !== 'it' && item.original_language !== 'en' ">{{item.original_language}}</p>
          <div class="star"> 
            <i
            v-for="(star, index) in 5"
            :key="index"
            class=" fa-star"
            :class="index < Math.round(item.vote_average / 2) ? 'fas' : 'far'"></i>
          </div>
          <h5>overview</h5>
          <div class="recensione">
            <p v-if="item.overview === '' ">Non ancora disponibile</p>
            <p v-else>{{item.overview}}</p>
          </div>

        </div>
      </div>
    </div>

  </div>

</template>

<script>
export default {
  nome: "Compilation",
  props:{
    item: Object
  },

}
</script>

<style lang="scss">
@import "../assets/style/mixins.scss";
@import '~@fontsource/roboto-condensed/index.css';
//per le stelline
@import '~@fortawesome/fontawesome-free/css/all.min.css';
.film{
  text-align: center;
  margin: 0 10px;
  font-family: 'Roboto Condensed', sans-serif;
  cursor: pointer;


  .flip-card {
    background-color: transparent;
    width: 175px;
    height: 220px;
    perspective: 1000px; 
  }

  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.6s;
    transform-style: preserve-3d;
    box-shadow: 0 4px 8px 0 rgb(50, 50, 50);
    border: 2px solid goldenrod;
    border-radius: 15px;

    img{
      width: 100%;
      height: 100%;
      border-radius: 15px;
    }
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
    border-radius: 15px;
  }

  .flip-card-front {
    background-color: #bbb;
    color: black;
  }

  .flip-card-back {
    background-color: black;
    color: white;
    transform: rotateY(180deg);
    padding: 5px;

    h2{
      font-size: 15px;
      text-transform: uppercase;
    }

    h4{
      text-transform: uppercase;
      font-size: 11px;
      padding: 2px 0;
    }

    .star{
      color: goldenrod;
      margin: 2px 0;
    }

    p{
      img{
        width: 20px;
        height: 10px;
        border-radius: 2px;
      }
    }

    h5{
      text-transform: uppercase;
    }

    .recensione{
      padding-top: 5px;
      height: 50%;
      width: 100%;
      overflow-y: auto;      

      p{
        ::-webkit-scrollbar-track {
          background: red;  
        }
      }

   
    }
  }
}
</style>