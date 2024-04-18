<script>
import {store} from '../store';
import axios from 'axios'

export default{
  data(){
    return{
      store: store,
    }
  },
  props:{
    genres: Object,
    id: Number
  },
  mounted(){
  },
  methods:{
    fetchMoviesByGenres(id){
      this.store.movies = [];
      axios.get('https://api.themoviedb.org/3/discover/movie?', {
        params:{
          api_key: '8c5d2929491cc6bc1823b19280c48648',
          with_genres: id
        }
      })
      .then((response)=>{
        // this.store.movies.push(response.data.results);
        this.store.movies = response.data.results;
        console.log("Movies results: ",  this.store.movies);
        // console.log("Genres fetch: ", response);
      });
    }
  }
}

</script>

<template>
  
  <ul class="genres-list">
    
    <li @click="fetchMoviesByGenres(genre.id)" v-for="genre in genres"><a href="#"> {{ genre.name }}</a><div class="line"></div></li>
    
  </ul>
  
  
</template>

<style scoped>
.genres-list{
  display: flex;
  align-items: center;
  

    li{
    font-weight: 600;
    padding: 10px 10px;
    /* display: flex;
    align-items: center; */
    }

    li .line::after{
      content: '';
      width: 100%;
      height: 2px;
      display: none;
      background: rgb(0,0,0);
      background: linear-gradient(90deg, rgba(0,0,0,0) 0%, rgba(255,255,255,1) 50%, rgba(0,0,0,0) 100%);
      margin: 0 auto;
    }

    li:hover .line::after{
      display: block;
    }

    
    
}
</style>

