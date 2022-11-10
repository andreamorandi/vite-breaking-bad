<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import CharactersList from "./components/CharactersList.vue";
import AppLoader from "./components/AppLoader.vue";
import { store } from "./store";

export default {
  components: {
    AppHeader,
    CharactersList,
    AppLoader
  },
  data() {
    return {
      store
    }
  },
  created() {
    this.store.loading = true;
    axios.get("https://www.breakingbadapi.com/api/characters").then((resp) => {
      this.store.characters = resp.data;
      console.log(this.store.characters);
      this.store.loading = false;
    });
  }
};
</script>

<template>
  <AppHeader />
  <main>
    <AppLoader v-if="store.loading" />
    <CharactersList v-else />
  </main>
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
</style>