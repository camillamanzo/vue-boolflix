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
    // search function that builds the Url according to what is typed and finds it in the movies API
    search(needle){
      axios.get(this.movieUrl,{
        params: {
          api_key: this.apikey,
          query: needle,
          language: "it-IT"
        }
      // then it spreads the content of the needle research to the movies array
      }).then(
        (response) => {
          this.movies = [...response.data.results]
        })
      // search function that builds the Url according to what is typed and finds it in the series API
      axios.get(this.seriesUrl,{
        params: {
          api_key: this.apikey,
          query: needle,
          language: "it-IT"
        }
      // then it spreads the content of the needle research to the series array
      }).then(
        (response) => {
          this.series = [...response.data.results]
        })
    }
  },
  // searches the API and spreads the contained objects to the home array for the home section (only displayed if the needle search isn't active)
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
