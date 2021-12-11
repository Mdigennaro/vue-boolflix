<template>
  <main>
    
    <h1>{{section}}</h1>

    <div class="container">


      <Compilation 
      v-for="item in listItem" 
      :key="item.id" 
      :item="item"
      />

    </div>


  </main>
</template>

<script>
import Compilation from './Compilation.vue';

export default {
  nome: "Main",
  
  components:{
    Compilation,
  },


  props:{
    listItem: Array,
    section: String
  },


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
  }
  
  .container{
    width: 100%;
    @include flex-between;
    justify-content: flex-start;
    overflow: hidden;
    padding: 10px;
    overflow-x: auto;
  
  }
  
}
</style>