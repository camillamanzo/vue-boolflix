<template>
  <div>
    <div class="container">
      <div class="row">
        <Card v-for="movie in movies" :key="movie.id" :movie="movie"/>
      </div>
    </div>
  </div>
</template>

<script>
import Card from "./Card";

export default {
  name: "Main",
  props: {
    movies : Array
  },
  components:{
    Card,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../style/variables.scss";
@import "../style/general.scss";

</style>
