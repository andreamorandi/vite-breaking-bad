<script>
export default {
    name: "CharacterCard",
    props: {
        character: Object
    }
}
</script>

<template>
    <div class="character-item text-center">
        <img :src="character.img" :alt="`${character.name} image`">
        <h5 class="m-3">{{ character.name }}</h5>
        <h6 class="text-secondary">{{ character.category }}</h6>
        <h6 class="text-secondary">{{ character.status }}</h6>
    </div>
</template>

<style lang="scss" scoped>
@use "../styles/partials/variables" as *;
.character-item {
    height: 450px;
    margin-top: 2rem;
    padding: 1rem;
    background-color: $primary-color;
}
</style>