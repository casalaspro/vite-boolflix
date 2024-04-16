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
    <div class="container">
      <div class="row">
        <AppCard 
          v-for="movie in store.movies"
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
.search-results{
  .row{
    margin-right: -10px;
    margin-left: -10px;
  }
}
</style>