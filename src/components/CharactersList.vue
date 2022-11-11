<script>
import { store } from "../store";
import CharacterCard from "./CharacterCard.vue";
import ResultMessage from "./ResultMessage.vue";

export default {
    name: "CharactersList",
    components: {
        ResultMessage,
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
    <div class="text-white py-4">
        <div class="container-90">
            <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 row-cols-xxl-5">
                <div class="col" v-for="character in store.characters" :key="character.char_id">
                    <CharacterCard :character="character"/>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>