<script>
import {store} from '../store';

export default{
  data(){
    return{
      
    }
  },
  props:{
    genres: Object
  },
  mounted(){
  }
}

</script>

<template>
  
  <ul class="genres-list">
    <li v-for="genre in genres"><a href="#"> {{ genre.name }}</a></li>
    
  </ul>
  
  
</template>

<style scoped>
.genres-list{
  display: flex;
  align-items: center;
  li{
    font-weight: 600;
    padding: 10px 10px;
    
    
    
    &::after{
      content: '';
      width: 10px;
      height: 2px;
      display: none;
      margin: 0 auto;
      background-color: white;
    }
    
  }
  li:hover + li::after{
    display: block;
  }
}
</style>

