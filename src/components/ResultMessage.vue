<script>
import { store } from "../store";

export default {
    name: "ResultMessage",
    data() {
        return {
            store
        }
    },
    computed: {
        charactersNumber() {
            return this.store.characters.length;
        }
    }
}
</script>

<template>
    <div class="found-characters">
        <div class="container-90">
            <h5 v-if="store.characters.length === 0">No results</h5>
            <h5 v-else>Found {{ charactersNumber }} {{charactersNumber === 1 ? 'character' : 'characters'}}</h5>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.found-characters {
    margin: 0 2rem;
    margin-top: 3rem;
    padding: 1.5rem .5rem;
    color: white;
    background-color: #212529;
    h5 {
        margin: 0;
    }
}
</style>