<script>
import axios from 'axios';
import {store} from '../store'


export default{
  data(){
    return{
  searchValue: '',
    }
  },
  methods:{
    fetchMovies(query){
      axios.get('https://api.themoviedb.org/3/search/movie?', {
        params:{
          api_key: '8c5d2929491cc6bc1823b19280c48648',
          query: query
        }
      })
      .then((response)=>{
        console.log(response);
        store.movies.push(response.data.results);
      })
    }
    
  },
  mounted(){
    this.fetchMovies("Il signore degli");
  },
  components:{
    
  }

}
</script>

<template>
  <div class="search-wrap">
    <input class="search-input" :value="searchValue" type="text">
    <button class="search-button">Search</button>
    <p>{{ searchValue }}</p>
  </div>
  
</template>

<style scoped>

</style>
