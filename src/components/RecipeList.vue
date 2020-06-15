<template>
    <div v-if="loading" class="recipe-list loading">
        <svg>
            <use href="icons.svg#icon-cw"></use>
        </svg>
    </div>
    <div v-else-if="recipes.length > 0" class="recipe-list">
        <p v-for="recipe in recipes" :key="recipe.recipe_id">{{recipe.title}}</p>
    </div>
    <div v-else class="recipe-list">
        <p>No recipes found.</p>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name: "RecipeList",
    props: [
        "search"
    ],
    data() {
        return {
            recipes: null
        }
    },
    computed: {
        loading() {
            return this.search && !this.recipes;
        }
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