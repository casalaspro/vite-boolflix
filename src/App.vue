<script>
import appSearch from './components/appSearch.vue'
import { store } from './store'

export default{
  data(){
    return{

    }
  },
  methods:{
    
  },
  components:{
    appSearch,
  },
  mounted(){
    console.log(store);
  }
}
</script>

<template>
  <appSearch/>
</template>

<style lang="scss">
@use './style/general'

</style>
