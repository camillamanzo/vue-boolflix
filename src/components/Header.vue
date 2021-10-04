<template>
  <header>
      <div>
          <img src="../assets/boolflix-logo.png" alt="boolflix logo">
      </div>
    <input type="text" placeholder="Search title" v-model="needle" @keyup.enter="$emit('search', needle)" class="mb-4">
    <button  @click="$emit('search', needle)">Search</button>
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
    text-align: center;

    img{
        padding-bottom: 20px;
        margin: auto;
    }
}
</style>