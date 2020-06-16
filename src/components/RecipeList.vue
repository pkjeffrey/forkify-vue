<template>
    <div v-if="loading" class="recipe-list loading">
        <svg>
            <use href="icons.svg#icon-cw"></use>
        </svg>
    </div>
    <div v-else-if="some" class="recipe-list">
        <RecipeItem v-for="recipe in recipes" :key="recipe.recipe_id" :recipe="recipe" @select="$emit('recipeSelected', $event)" />
    </div>
    <div v-else class="recipe-list">
        <p>No recipes found.</p>
    </div>
</template>

<script>
import axios from "axios";
import RecipeItem from "./RecipeItem";

export default {
    name: "RecipeList",
    components: {RecipeItem},
    props: ["search"],
    data() {
        return {
            recipes: null
        }
    },
    computed: {
        loading() {return this.search && !this.recipes},
        some() {return this.recipes && this.recipes.length > 0}
    },
    mounted() {
        if (this.search) {
            axios.get(`https://forkify-api.herokuapp.com/api/search?q=${this.search}`)
                .then(response => {
                    this.recipes = response.data.recipes;
                })
                .catch(err => {
                    console.log(err);
                    this.recipes = [];
                });
        }
    }
}
</script>