<template>
  <div class="col-3 poster-wrapper">
    <ul class="p-4 ">
      <!-- poster image .d-none when hover -->
      <li><img v-if="element.poster_path" class="poster-img img-fluid" :src="thumbsUrl + element.poster_path" :alt="element.title ? element.title : element.name"></li>
      <li>
        <!-- info section only displayed on hover. -->
        <ul class="hover-display">
          <li><h2>{{ element.title ? element.title : element.name }}</h2></li>
          <!-- v-if-else for flag img. -->
          <li v-if="element.original_language == 'it'">Language: {{ element.original_language.toUpperCase() }} <img class="flag-img" src="../assets/it-flag.png" alt="it flag"></li>
          <li v-else-if="element.original_language == 'en'">Language: {{ element.original_language.toUpperCase() }} <img class="flag-img" src="../assets/uk-flag.png" alt="uk flag"></li>
          <li v-else >Original language: {{ element.original_language.toUpperCase() }}</li>
          <!-- /v-if-else -->
          <li>Original title: {{ element.original_title }}</li>
          <!-- li with stars for the vote -->
          <li>
              <span><i v-for="index in Math.round((element.vote_average)/2)" :key="index" class="fas fa-star yellow-text"></i></span>
              <span><i v-for="index in 5 - Math.round((element.vote_average)/2)" :key="index" class="far fa-star"></i></span> 
          </li>
        </ul>
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
      thumbsUrl: "https://image.tmdb.org/t/p/w342",
    }
  }
}
</script>

<style scoped lang="scss">
@import "../style/variables.scss";
@import "../style/general.scss";

ul{
    list-style: none;
    color: $text-color;
    
    .poster-img{
        width: 100%;
        box-shadow: 5px 5px 5.5px black;
        // border: 1px solid $text-color;
    }
    .flag-img{
        width: 30px;
    }
    .yellow-text{
      color: rgb(255, 208, 0);
    }
}
.poster-wrapper:hover .poster-img{
      display: none;
    }
    .hover-display{
      display: none;
    }
    .poster-wrapper:hover .hover-display{
      display: block;
    }
</style>