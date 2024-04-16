<script>
import appSearch from './components/appSearch.vue'
import appNavbar from './components/appNavbar.vue'
import appMain from './components/appMain.vue'
import appFooter from './components/appFooter.vue'
import { store } from './store'
import axios from 'axios'

export default{
  data(){
    return{

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
  components:{
    appSearch,
    appNavbar,
    appMain,
    appFooter

  },
  mounted(){
    console.log(store);
    this.fetchMovies("Il signore degli");
    console.log(store.movies);
    
  }
}
</script>

<template>

    <appNavbar/>
    <appMain/>
    <appFooter/>
    

</template>

<style lang="scss">
@use './style/general'

</style>
