<template>
  <main>
    <div class="fluid-container">
      <!-- Main section only visible at the beginning -->
      <div class="row" id="home-section">
        <Home :class="needle > 0 ? d-none : d-block" v-for="movie in home" :key="movie.id" :movie="movie"/>
      </div>
      <!-- Movies section -->
      <div class="row" id="movies-section">
        <Card v-for="element in movies" :key="element.id" :element="element"/>
      </div>
      <!-- Series section -->
      <div class="row" id="series-section">
        <Card v-for="element in series" :key="element.id" :element="element"/>
      </div>
    </div>
  </main>
</template>

<script>
import Card from "./Card";
import Home from "./Home";

export default {
  name: "Main",
  props: {
    movies : Array,
    series : Array,
    home : Array,
  },
  components:{
    Card,
    Home,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../style/variables.scss";
@import "../style/general.scss";
main{
  height: 100vh;
  background-color: $main-bg;

  .fluid-container{
    background-color: $main-bg;
  }
}

</style>
