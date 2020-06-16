<template>
  <div id="app" class="App">
    <header class="App-header">
      <img src="favicon.png" alt="logo" title="Forkify in Vue">
      <h1>Forkify in Vue</h1>
      <Search @search="onSearch" />
    </header>
    <RecipeList :key="search" :search="search" @recipeSelected="onRecipeSelected" />
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
      search: null,
      selectRecipe: null
    };
  },
  methods: {
    onSearch(query) {
      this.search = query;
    },
    onRecipeSelected(id) {
      this.selectRecipe = id;
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
.recipe-list {
  width: 30%;
  float: left;
  overflow: hidden;
}
</style>
