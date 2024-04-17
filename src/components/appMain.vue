<script>
import AppCard from './appCard.vue';
import {store} from '../store'


export default{
  data(){
    return{
      store : store,

    }
  },
  components:{
    AppCard
  },
  created(){
    // console.log("Dal'appMain ",  dbMovies);
  },
}

</script>

<template>

  <section class="search-results">
    <div class="movies">
      <div class="container">
        <h1 class="movie-title">Movies</h1>
        <div class="row">
          <AppCard 
            v-for="movie in store.movies"
            :movieTitle="movie.title"
            :movieOriginalTitle="movie.original_title"
            :movieLanguage="movie.original_language"
            :movieVote="movie.vote_average"
            :moviePoster="movie.poster_path"
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
          />
        </div>
      </div>
    </div>
  </section>

</template>

<style lang="scss" scope>
.search-results{
  .row{
    margin-right: -10px;
    margin-left: -10px;
  }
}
</style>