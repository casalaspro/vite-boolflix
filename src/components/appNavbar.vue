

<script>
  import appSearch from './appSearch.vue'
  export default{
    data(){
      return{

      }
    },
    components:{
      appSearch
    }
  }

</script>

<template>
<nav>
  <div class="container">
    <div class="row">
      <div class="logo"></div>
      <ul class="menu">
        <li>Home</li>
        <li>Serie TV</li>
        <li>Film Nuovi e popolari</li>
        <li>La mia lista</li>
        <li>Sfoglia per lingua</li>
      </ul>
      <appSearch/>
    </div>
  </div>
</nav>

</template>

<style lang="scss" scope>

</style>