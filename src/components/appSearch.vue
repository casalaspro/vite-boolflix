<script>
import axios from 'axios';
import {store} from '../store'


export default{
  data(){
    return{
      store: store,
      searchValue: '',

    }
  },
  methods:{
    fetchMovies(query){
      this.store.movies = [];
      axios.get('https://api.themoviedb.org/3/search/movie?', {
        params:{
          api_key: '8c5d2929491cc6bc1823b19280c48648',
          query: query
        }
      })
      .then((response)=>{
        // this.store.movies.push(response.data.results);
        for(let i= 0; i<response.data.results.length; i++){
          this.store.movies.push(response.data.results[i]);
        }
        console.log("response.data.results: ", response.data.results);
        console.log("Dentro store.movie[0]: ", store.movies[0]);
      });
      axios.get('https://api.themoviedb.org/3/search/tv?', {
        params:{
          api_key: '8c5d2929491cc6bc1823b19280c48648',
          query: query
        }
      })
      .then((response)=>{
        // this.store.movies.push(response.data.results);
        
        const newNameArray = response.data.results.map(({
        name: title,
        original_name: original_title,
          ...rest
          }) => ({
            title,
            original_title,
          ...rest
          }));
        console.log(newNameArray)
        // for(let i= 0; i<response.data.results.length; i++){
        //   this.store.movies.push(response.data.results[i]);
        // }
        this.store.tvSeries = newNameArray;
        console.log("response.data.results: ", response.data.results);
        // console.log("Dentro store.movie[0]: ", store.movies[0]);
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
  .search-input{
    border: 1px solid white;
    height: 30px;
    background-color: rgba(0, 0, 0, 0);
    color: white;
    &:focus-visible{
      outline: none;
      padding: 3px 5px;
    }
  }
</style>
