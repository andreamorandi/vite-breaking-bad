<script>
import { store } from "../store";
import CharacterCard from "./CharacterCard.vue";

export default {
    name: "CharactersList",
    components: {
        CharacterCard
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="container bg-white text-white py-4">
        <div class="container-90">
            <div class="found-characters">
                <span>Found 62 characters</span>
            </div>
            <div class="row row-cols-1 row-cols-sm-2 row-cols-md-4 row-cols-lg-5">
                <div class="col" v-for="character in store.characters" :key="character.char_id">
                    <CharacterCard :character="character"/>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .container-90 {
        width: 90%;
        margin: 0 auto;
        .found-characters {
            margin-top: 2rem;
            padding: 1rem .5rem;
            background-color: #212529;
        }
    }
</style>