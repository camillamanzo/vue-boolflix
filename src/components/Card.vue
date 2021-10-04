<template>
  <div class="col-4">
      <h2>{{ movie.title }}</h2>
      <ul>
          <li>Original title: {{ movie.original_title }}</li>
          <li>Language: {{ movie.original_language }}</li>
          <li>Ratings: {{ movie.vote_average }}/10</li>
      </ul>
      
      
      
  </div>
</template>

<script>
export default {
    name: "Card",
    props: ["movie"]
}
</script>

<style scoped lang="scss">
@import "../style/variables.scss";
@import "../style/general.scss";

</style>