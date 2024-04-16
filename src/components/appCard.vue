<script>
export default{
  data(){
    return{

    }
  },
  methods:{
    
  },
  props:{
    movieTitle: String,
    movieOriginalTitle: String,
    movieLanguage: String,
    movieVote: Number
  }

}
</script>

<template>
  <div class="col-20">
    <div class="card">

      <h1>{{ movieTitle }}</h1>
      <h2>{{ movieOriginalTitle }}</h2>
      <h3>{{ movieLanguage }}</h3>
      <h4>{{ movieVote }}</h4>

    </div>
  </div>


  
</template>

<style scoped>
.card{
  border: 1px solid white;
  height: 100%;
}
</style>
