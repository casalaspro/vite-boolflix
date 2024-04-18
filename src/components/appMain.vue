<script>
import AppCard from './appCard.vue';
import {store} from '../store';
import AppGenres from './appGenres.vue';
import axios from 'axios'


export default{
  data(){
    return{
      store : store,
      genres : store.genres
      
    }
  },
  components:{
    AppCard,
    AppGenres
  },
  created(){
    // console.log("Dal'appMain ",  dbMovies);
    this.fetchGenres();
  },
  methods:{
    fetchGenres(){
      // this.store.genres = [];
      axios.get('https://api.themoviedb.org/3/genre/movie/list?', {
        params:{
          api_key: '8c5d2929491cc6bc1823b19280c48648',
          language: 'en'
        }
      })
      .then((response)=>{
        // this.store.movies.push(response.data.results);
        this.store.genres = response.data.genres;
        console.log("Genres: ", this.store.genres);
        // console.log("Genres fetch: ", response);
      });
    },

    getStars(voteOn10){
      const voteOn5 = Math.floor(voteOn10 / 2);
      return voteOn5;
    }

  }
}

</script>

<template>

  <section class="search-results">
    <div class="movies">
      <div class="container">
        <h1 class="movie-title">Movies</h1>
        <AppGenres 
        :genres="store.genres"
        />
        <div class="row">
          <AppCard 
            v-for="movie in store.movies"
            :movieTitle="movie.title"
            :movieOriginalTitle="movie.original_title"
            :movieLanguage="movie.original_language"
            :movieVote="movie.vote_average"
            :moviePoster="movie.poster_path"
            :fullStars="getStars(movie.vote_average)"
            :halfStars="5-getStars(movie.vote_average)"
            :overview="movie.overview"
          />
        </div>
      </div>
    </div>

    <div class="tv-series">
      <div class="container">
        <h1 class="tv-title">Tv Series</h1>
        <div class="row">
          <AppCard 
            v-for="movie in store.tvSeries"
            :movieTitle="movie.title"
            :movieOriginalTitle="movie.original_title"
            :movieLanguage="movie.original_language"
            :movieVote="movie.vote_average"
            :moviePoster="movie.poster_path"
            :fullStars="getStars(movie.vote_average)"
            :halfStars="5-getStars(movie.vote_average)"
            :overview="movie.overview"
          />
        </div>
      </div>
    </div>
  </section>

</template>

<style lang="scss" scope>
.search-results{
  padding-top: 71px;
  h1::after{
      content: '';
      display: block;
      background: rgb(255,255,255);
      background: linear-gradient(90deg, rgba(255,255,255,1) 0%, rgba(217,217,217,1) 51%, rgba(0,0,0,0) 100%);

      width: 100%;
      height: 2px;
      margin-bottom: 3px;
    }
  
  .row{
    margin-right: -5px;
    margin-left: -5px;
  }
}
</style>