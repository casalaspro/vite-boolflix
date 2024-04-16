<script>
import AppCard from './appCard.vue';
import {store} from '../store'


export default{
  data(){
    return{
      dbMovies : store.movies[0],

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
    <div class="container">
      <div class="row">
        <AppCard 
          v-for="movie in dbMovies"
          :movieTitle="movie.title"
          :movieOriginalTitle="movie.original_title"
          :movieLanguage="movie.original_language"
          :movieVote="movie.vote_average"


        />
      </div>
      <!-- v-if="dbMovies.length !== 0" -->
    </div>
  </section>

</template>

<style lang="scss" scope>

</style>