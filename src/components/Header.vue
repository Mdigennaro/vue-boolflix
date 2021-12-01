<template>
  
  <header>

    <div class="h-left">
      <img src="" alt="logo">
    </div>

    <div class="h-right">
      <input type="text" placeholder="Ricerca film">
      <button>search</button>
    </div>

  </header>

</template>

<script>
export default {
  nome: "Header"
}
</script>

<style lang="scss">
@import "../assets/style/mixins.scss" ;
  header{
    padding: 20px;
    height: 80px;
    background-color: black;
    @include flex-between ;   
  }
</style>