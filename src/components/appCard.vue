<script>
export default{
  data(){
    return{
      isFlag: true,
      posterDimension: "w154",
      starsArray: []
    }
  },
  methods:{
    getPosterSource(dimensionsString, queryString){
      const srcBase = "https://image.tmdb.org/t/p/";
      return new URL(srcBase + dimensionsString + queryString, import.meta.url).href;
    },
    getImgSource(string){
      const src = "../assets/";
      const englandFlag = "gbr.svg";
      const italyFlag = "ita.svg";
      if(string === "en"){
        return new URL(src + englandFlag, import.meta.url).href
      }else if(string === "it"){
        return new URL(src + italyFlag, import.meta.url).href;
      }else{
        this.isFlag = false
      }
    }
  },
  mounted(){
    console.log("Test Immagine: ", this.getPosterSource("w92", "/vCTk3LfY2Ux7IngTTUSxejLcSJW.jpg"));
  },
  props:{
    movieTitle: String,
    movieOriginalTitle: String,
    movieLanguage: String,
    movieVote: Number,
    moviePoster: String
  }

}
</script>

<template>
  <div class="col-20">
    <div class="card">

      <h1>{{ movieTitle }}</h1>
      <h2>{{ movieOriginalTitle }}</h2>
      <!-- <h3>{{ movieLanguage }}</h3> -->
      <img v-if="isFlag" class="flag" :src="getImgSource(movieLanguage)" alt="">
      <h3 v-else>{{ movieLanguage }}</h3>
      <h4>{{ Math.floor(movieVote) }}</h4>
      <img :src="getPosterSource(posterDimension, moviePoster)" alt="" class="poster">
      <font-awesome-icon :icon="['far', 'star']" />
      
    </div>
  </div>


  
</template>

<style scoped>
.col-20{
  /* border: 1px solid rgba(255, 255, 255, 0.32); */
  padding: 10px;
  .card{
    h1{
      font-size: 17px;
    }
    h2{
      font-style: italic;
      font-size: 15px;
    }
    img{
      &.flag{
        width: 31px;
      }
    }
    border: 1px solid rgba(255, 255, 255, 0.32);
    height: 100%;
    /* aspect-ratio: 1/1.5; */
    padding: 10px;
    

      & > *{
        margin-bottom: 20px;
      }
  }
}
</style>

<!-- 
  POSTER SIZES

  "w92", "w154", "w185", "w342", "w500", "w780", "original" 

-->
