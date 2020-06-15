<template>
  <div id="app" class="App">
    <header class="App-header">
      <img src="favicon.png" alt="logo" title="Forkify in Vue">
      <h1>Forkify in Vue</h1>
      <Search v-on:onSearch="onSearch" />
    </header>
    <RecipeList :key="search" v-bind:search="search" />
  </div>
</template>

<script>
import Search from "./components/Search";
import RecipeList from "./components/RecipeList";

export default {
  name: "App",
  components: {
    Search,
    RecipeList
  },
  data() {
    return {
      search: null
    };
  },
  methods: {
    onSearch(query) {
      this.search = query;
    }
  }
}
</script>

<style>
.App {
  margin: 1rem 2rem;
}
.App-header {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}
.App-header img {
  width: 50px;
  height: 50px;
  margin-right: 1rem;
}
.App-header h1 {
  margin-right: 2rem;
}
.App-header input {
  font-size: 1.2rem;
}
</style>
