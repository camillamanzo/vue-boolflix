<template>
  <div id="app">
    <Header @search="search"/>
    <Main :movies="movies" :series="series" :home="home"/>
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
  data() {
    return{
      movieUrl: "https://api.themoviedb.org/3/search/movie",
      seriesUrl: "https://api.themoviedb.org/3/search/tv",
      apikey: "8a80fdb66a4a7b020a3f11d8964099ab",
      movies: [],
      series: [],
      home: [],
    }
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
  created(){
      axios.get("https://api.themoviedb.org/3/search/movie?api_key=8a80fdb66a4a7b020a3f11d8964099ab&query=back+to+the+future")
      .then((response) => { 
      this.home = [...response.data.results]
      console.log(this.home)
    })
  },
  
}
</script>

<style lang="scss">
@import "./style/variables.scss";
@import "./style/general.scss";

</style>
