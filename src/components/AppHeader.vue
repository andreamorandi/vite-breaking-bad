<script>
export default {
    name: "AppHeader",
    data() {
            return {
                logo: "breaking-bad-logo.png"
            }
        },
        methods: {
            getImagePath(image) {
                return new URL(`../assets/img/${image}`, import.meta.url).href;
            }
        }
}
</script>

<template>
    <header>
        <img :src="getImagePath(logo)" alt="breaking bad logo">
        <h1>Breaking Bad Api</h1>
    </header>
</template>

<style lang="scss" scoped>
header {
    img {
        height: 5rem;
        margin-left: 1rem;
    }
    h1 {
        display: inline-block;
        font-weight: 600;
        line-height: 5rem;
        vertical-align: middle;
        margin-left: 1rem;
        color: white;
    }
}
</style>