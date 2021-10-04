<template>
  <div id="app">
    <Header @search="search"/>
    <Main :movies="movies" :series="series"/>
  </div>
</template>

<script>
import Main from "./components/Main.vue"
import Header from "./components/Header.vue"
import axios from "axios"

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  methods: {
    search(needle){
      axios.get(this.movieUrl,{
        params: {
          api_key: this.apikey,
          query: needle,
          language: "it-IT"
        }
      }).then(
        (response) => {
          this.movies = [...response.data.results]
        })
    
      axios.get(this.seriesUrl,{
        params: {
          api_key: this.apikey,
          query: needle,
          language: "it-IT"
        }
      }).then(
        (response) => {
          this.series = [...response.data.results]
        })
    }
  },
  data() {
    return{
      movieUrl: "https://api.themoviedb.org/3/search/movie",
      seriesUrl: "https://api.themoviedb.org/3/search/tv",
      apikey: "8a80fdb66a4a7b020a3f11d8964099ab",
      movies: [],
      series: [],
    }
  }
}
</script>

<style lang="scss">
@import "./style/variables.scss";
@import "./style/general.scss";
#app {


  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 60px;
}
</style>
