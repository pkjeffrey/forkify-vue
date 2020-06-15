<template>
    <form v-on:submit.prevent="onSubmit">
        <input type="text" size="25" v-model.trim="query" placeholder="Search over 1,000,000 recipes">
    </form>
</template>

<script>
export default {
    name: "Search",
    data() {
        return {
            query: ""
        };
    },
    methods: {
        onSubmit() {
            if (this.query) {
                this.$emit("onSearch", this.query);
            }
            this.query = "";
        }
    }
}
</script>