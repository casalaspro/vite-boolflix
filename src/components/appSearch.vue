<script>
import axios from 'axios';
import {store} from '../store'


export default{
  data(){
    return{
      searchValue: '',
      movieDatabase: store.movies,

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
        store.movies.push(response.data.results);
        console.log("response.data.results: ", response.data.results);
        console.log("Dentro store.movie[0]: ", store.movies[0]);
      })
    }
    
  },
  mounted(){
    // this.fetchMovies("Il signore degli");
  },
  components:{
    
  }

}
</script>

<template>
  <div class="search-wrap">
    <input class="search-input" v-model="searchValue" type="text">
    <button @click="fetchMovies(searchValue)" class="search-button">Search</button>
    <!-- <p v-if="movieDatabase.length !== 0">{{ movieDatabase }}</p> -->
  </div>
  
</template>

<style scoped>

</style>
