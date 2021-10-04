<template>
  <div>
    <div class="container">
      <div class="row">
        <h1 class="text-center mb-3">Movies with this title:</h1>
        <Card v-for="element in movies" :key="element.id" :element="element"/>
        <h1  class="text-center mb-3">TV Series with this title:</h1>
        <Card v-for="element in series" :key="element.id" :element="element"/>
      </div>
    </div>
  </div>
</template>

<script>
import Card from "./Card";

export default {
  name: "Main",
  props: {
    movies : Array,
    series : Array,
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
