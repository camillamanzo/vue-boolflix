<template>
    <div class="col-3 poster-wrapper">
        <ul class="p-4 ">
            <!-- poster image .d-none when hover -->
            <li><img class="poster-img img-fluid" :src="(thumbsUrlHome) + movie.poster_path" :alt="movie.title"></li>
            <li>
            <!-- info section only displayed on hover. -->
                <ul class="hover-display">
                    <li><h2>{{ movie.title }}</h2></li>
                    <li>Language: {{ movie.original_language.toUpperCase() }} <img class="flag-img" src="../assets/uk-flag.png" alt="uk flag"></li>
                    <li>Original title: {{ movie.original_title }}</li>
                    <!-- li with stars for the vote -->
                    <li>
                        <span><i v-for="index in Math.round((movie.vote_average)/2)" :key="index" class="fas fa-star yellow-text"></i></span>
                        <span><i v-for="index in 5 - Math.round((movie.vote_average)/2)" :key="index" class="far fa-star"></i></span> 
                    </li>
                </ul>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Home",
    props: ["movie"],
    data() {
        return{
        thumbsUrlHome: "https://image.tmdb.org/t/p/w342",
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