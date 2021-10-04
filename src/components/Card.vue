<template>
  <div class="col-3">
      
      <ul>
            <li><img class="poster-img" :src="thumbsUrl + element.poster_path" alt=""></li>
            <li><h2>{{ element.title ? element.title : element.name }}</h2></li>
            
            <li v-if="element.original_language == 'it'">Language: {{ element.original_language.toUpperCase() }} <img class="flag-img" src="../assets/it-flag.png" alt="it flag"></li>
            <li v-else-if="element.original_language == 'en'">Language: {{ element.original_language.toUpperCase() }} <img class="flag-img" src="../assets/uk-flag.png" alt="uk flag"></li>
            <li v-else >Original language: {{ element.original_language.toUpperCase() }}</li>
            
            <li>Original title: {{ element.original_title }}</li>
            <li>
                <span><i v-for="index in Math.round((element.vote_average)/2)" :key="index" class="fas fa-star yellow-text"></i></span>
                <span><i v-for="index in 5 - Math.round((element.vote_average)/2)" :key="index" class="fas fa-star"></i></span> 
            </li>
      </ul>

  </div>
</template>

<script>
export default {
    name: "Card",
    props: ["element"],
    data() {
    return{
      thumbsUrl: "https://image.tmdb.org/t/p/w500",
    }
  }
}
</script>

<style scoped lang="scss">
@import "../style/variables.scss";
@import "../style/general.scss";

ul{
    list-style: none;
    .poster-img{
        width: 100%;
    }
    .flag-img{
        width: 30px;
    }
    .yellow-text{
      color: rgb(255, 208, 0);
    }
}

</style>