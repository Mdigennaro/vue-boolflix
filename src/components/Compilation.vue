<template>

  <div class="film">

    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`" :alt="item.title || item.name">
        </div>
        <div class="flip-card-back">

          <h2>{{item.title || item.name }}</h2>
          <h4>{{item.original_title || item.original_name}}</h4>
          <p v-if="item.original_language === 'it' "><img src="../assets/img/it.png" :alt="item.original_language"></p>
          <p v-if="item.original_language === 'en' "><img src="../assets/img/en.png" :alt="item.original_language"></p>
          <p v-if="item.original_language !== 'it' && item.original_language !== 'en' ">{{item.original_language}}</p>
          <p>{{Math.round(item.vote_average / 2)}}</p>
          <div> 
            <i
            v-for="(star, index) in 5"
            :key="index"
            class=" fa-star"
            :class="index < Math.round(item.vote_average / 2) ? 'fas' : 'far'"></i>
          </div>
          <div class="recensione">
            <p>{{item.overview}}</p>
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


@import '~@fortawesome/fontawesome-free/css/all.min.css';
.film{
  text-align: center;
  margin: 0 10px;

  .flip-card {
    background-color: transparent;
    width: 250px;
    height: 278px;
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

    img{
      width: 100%;
      height: 100%;
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
    p{
      img{
        width: 30px;
        border-radius: 2px;
      }
    }

    .recensione{
      height: 50%;
      width: 100%;
      overflow-y:scroll;
      
    }
  }
  
}
</style>