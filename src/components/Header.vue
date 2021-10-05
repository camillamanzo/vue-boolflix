<template>
  <!-- Header with nav-bar and search function. -->
  <header>
    <nav class="navbar navbar-expand-lg">
      <div class="container-fluid">
        <!-- Logo. -->
        <img src="../assets/boolflix-logo.png" alt="boolflix logo">
        <div class="navbar-collapse">
          <!-- list with nav items -->
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link text-light" href="#home-section">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link text-light" href="#movies-section">Movies</a>
            </li>
            <li class="nav-item">
              <a class="nav-link text-light" href="#series-section">Series</a>
            </li>
          </ul>
          <form class="d-flex">
            <input class="form-control me-2" type="text" placeholder="Search title" v-model="needle" @keyup.enter="$emit('search', needle)">
            <button class="btn btn-outline-danger" type="submit" @click="$emit('search', needle)">Search</button>
          </form>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Header",
  
  data(){
    return {
      needle: "",
    }
  },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../style/variables.scss";
@import "../style/general.scss";

header{
  // height: 80px;
  background-color: $header-bg;
  color: $text-color;

  ul{
    display: flex;
    text-align: center;
    align-items: center;
    justify-content: space-between;

    list-style: none;

  }
  img{
      margin: auto;
      width: 100px;
  }
}
</style>