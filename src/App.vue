<template>
  <div id="app">
    <Header @search="search"/>
    <Main :movies="movies"/>
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
          console.log(this.movies)
        }
      )
    }
  },
  data() {
    return{
      movieUrl: "https://api.themoviedb.org/3/search/movie",
      seriesUrl: "",
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
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
