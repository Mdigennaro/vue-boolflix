<template>
  <main>
    
    <h1>{{section}}</h1>

    <div class="container">

      <VueSlickCarousel v-bind="settings">

        <Compilation 
        v-for="item in listItem" 
        :key="item.id" 
        :item="item"
        />

      </VueSlickCarousel>  

    </div>


  </main>
</template>

<script>
import Compilation from './Compilation.vue';
import VueSlickCarousel from 'vue-slick-carousel';
import 'vue-slick-carousel/dist/vue-slick-carousel.css';
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
  nome: "Main",
  
  components:{
    Compilation,
    VueSlickCarousel
  },


  props:{
    listItem: Array,
    section: String
  },

  data() {
    return {
      settings:{
        "dots": true,
        "infinite": false,
        "speed": 500,
        "slidesToShow": 4,
        "slidesToScroll": 4,
        "initialSlide": 0,
        "responsive": [{
          "breakpoint": 1024,
          "settings": {
            "slidesToShow": 3,
            "slidesToScroll": 3,
            "infinite": true,
            "dots": true
          }
        },
        {
          "breakpoint": 600,
          "settings": {
            "slidesToShow": 2,
            "slidesToScroll": 2,
            "initialSlide": 2
          }
        },
        {
          "breakpoint": 480,
          "settings": {
            "slidesToShow": 1,
            "slidesToScroll": 1
          }
        }]
      }
    }
  }
}


</script>

<style lang="scss">
@import '~@fontsource/roboto-condensed/700.css';
@import "../assets/style/mixins.scss";

main{
  width: 1015px;
  margin: 0 auto;
  text-align: start;
  padding: 10px;

  h1{
    color: goldenrod;
    font-family: 'Roboto Condensed', sans-serif;
    padding: 10px 0;
  }

}
</style>