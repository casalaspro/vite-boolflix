<script>
export default{
  data(){
    return{
      isFlag: true,
    }
  },
  methods:{
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
      <!-- <h3>{{ movieLanguage }}</h3> -->
      <img v-if="isFlag" class="flag" :src="getImgSource(movieLanguage)" alt="">
      <h3 v-else>{{ movieLanguage }}</h3>
      <h4>{{ movieVote }}</h4>
      
    </div>
  </div>


  
</template>

<style scoped>
.card{
  img{
    &.flag{
      width: 31px;
    }
  }
  border: 1px solid white;
  height: 100%;
}
</style>
