<template>
    <div class="recipe-list" @click="$emit('select', recipe.recipe_id)">
        <figure><img :src="recipe.image_url" :alt="recipe.title"></figure>
        <div>
            <h1>{{recipe.title}}</h1>
            <p>{{recipe.publisher}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "RecipeItem",
    props: ["recipe"]
}
</script>

<style scoped>
.recipe-list {
    width: 100%;
    height: 80px;
    margin-right: 1rem;
    cursor: pointer;
}
figure {
    width: 50px;
    height: 50px;
    overflow: hidden;
    border-radius: 25px;
    float: left;
    margin-right: 1rem;
}
img {
    width: 100%;
    transform: scale(2);
}
h1 {
    font-size: 1rem;
}
</style>