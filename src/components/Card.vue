<template>
  <div class="col-4">
      
      <ul>
            <li><h2>{{ element.title ? element.title : element.name}}</h2></li>
            
            <li v-if="element.original_language == 'it'">Language: {{ element.original_language.toUpperCase() }} <img src="../assets/it-flag.png" alt="it flag"></li>
            <li v-else-if="element.original_language == 'en'">Language: {{ element.original_language.toUpperCase() }} <img src="../assets/uk-flag.png" alt="uk flag"></li>
            <li v-else >Original language: {{ element.original_language.toUpperCase() }}</li>
            
            <li>Original title: {{ element.original_title }}</li>
            <li>Ratings: {{ element.vote_average / 2 }}/5</li>
      </ul>

  </div>
</template>

<script>
export default {
    name: "Card",
    props: ["element",]
}
</script>

<style scoped lang="scss">
@import "../style/variables.scss";
@import "../style/general.scss";

ul{
    list-style: none;
    
    img{
        width: 20px;
    }
}

</style>