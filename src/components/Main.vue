<template>
  <main>
    
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

  },


}


</script>

<style lang="scss">
@import "../assets/style/mixins.scss";
main{
  height: 45%;
  
  .container{
    width: 100%;
    height:50%;
    @include flex-between;
    justify-content: flex-start;
    overflow: hidden;
    overflow-x: scroll;
    padding: 10px;
  
  }
  
}
</style>