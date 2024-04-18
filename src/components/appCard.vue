<script>
export default{
  data(){
    return{
      isFlag: true,
      posterDimension: "w342",
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
  },
  props:{
    movieTitle: String,
    movieOriginalTitle: String,
    movieLanguage: String,
    movieVote: Number,
    moviePoster: String,
    fullStars: Number,
    halfStars: Number,
    overview: String
  }

}
</script>

<template>
  <div class="col-20">
    <div class="card">
      <img :src="getPosterSource(posterDimension, moviePoster)" alt="" class="poster">
      <div class="card-body">

        <p><b>Titolo: </b>{{ movieTitle }}</p>
        <p><b>Titolo originale: </b>{{ movieOriginalTitle }}</p>
        <!-- <h3>{{ movieLanguage }}</h3> -->
        <div  v-if="isFlag" class="language">
          <p class=""><b>Lingua: </b></p><img  class="flag" :src="getImgSource(movieLanguage)" alt="">
        </div>
        <div v-else class="language">
          <p><b>Lingua: </b>{{ movieLanguage }}</p>
        </div>
        <p><b>Voto: </b>
          <font-awesome-icon v-for="n in fullStars" v-if="fullStars > 0" :icon="['fas', 'star']" />
          <font-awesome-icon v-for="n in halfStars" v-if="halfStars > 0" :icon="['far', 'star']" />
        </p>
        <p><b>Overview: </b>{{ overview }}</p>
      
      </div>
    </div>
  </div>


  
</template>

<style scoped>
.col-20{
  /* border: 1px solid rgba(255, 255, 255, 0.32); */
  padding: 5px;

  .card{
    position: relative;
    .card-body{
      position: absolute;
      top: 0;
      background-color: rgba(0, 0, 0, 0.879);
      z-index: 1;
      width: 100%;
      height: 100%;
      padding: 10px 10px;
      opacity: 0;
      transition: opacity 0.7s;
      &:hover{
        opacity: 1;
      }
    }
    .language{
      display: flex;
      align-items: center;
    }
    
    img{
      /* border: 1px solid rgba(255, 255, 255, 0.32); */
      height: 100%;
      position: relative;
       
      &.flag{
        width: 31px;
        margin-left: 4px;
      }
        
      &.poster{
        width: 100%;
      }

      & > *{
        margin-bottom: 20px;
      }
    }
  }
}
</style>

<!-- 
  POSTER SIZES

  "w92", "w154", "w185", "w342", "w500", "w780", "original" 

-->
