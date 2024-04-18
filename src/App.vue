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
    
  },
  components:{
    appSearch,
    appNavbar,
    appMain,
    appFooter

  },
  mounted(){
    console.log(store);
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
@use './style/general';

.container{
  width: 90%;
  margin: 0 auto;
}

</style>
