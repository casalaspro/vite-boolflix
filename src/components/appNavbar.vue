

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
    <div class="row navbar align-center space-between">
      <div class="logo">Boolzapp</div>
      <ul class="menu">
        <li><a href="#">Home</a></li>
        <li><a href="#">Serie TV</a></li>
        <li><a href="#">Film Nuovi e popolari</a></li>
        <li><a href="#">La mia lista</a></li>
        <li><a href="#">Sfoglia per lingua</a></li>
      </ul>
      <appSearch/>
    </div>
  </div>
</nav>

</template>

<style lang="scss" scope>
// @import '../style/_variables.scss';

  nav{
    .logo{
      // color: $company-color;
      color: red;
      font-weight: 900;
      font-size: 30px;
      letter-spacing: 3px;
    }
    margin: 40px 0;
    .menu{
      display: flex;
      justify-content: center;
      align-items: center;
      li{
        padding: 5px;
        line-height: 10px;
      }
    }
  }

</style>