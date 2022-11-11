<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import CharactersList from "./components/CharactersList.vue";
import AppLoader from "./components/AppLoader.vue";
import AppSearch from "./components/AppSearch.vue";
import ResultMessage from "./components/ResultMessage.vue";
import { store } from "./store";

export default {
  components: {
    AppHeader,
    AppSearch,
    ResultMessage,
    CharactersList,
    AppLoader
  },
  data() {
    return {
      store
    }
  },
  created() {
    this.getCharacters();
  },
  methods: {
    getCharacters() {
      this.store.loading = true;
      let apiUrl = "https://www.breakingbadapi.com/api/characters";
      const urlParams = {
        ...this.store.searchKey && {name: this.store.searchKey},
        ...this.store.searchCategory && {category: this.store.searchCategory}
      }
      axios.get(apiUrl, {
        params: urlParams
      }).then(
        (resp) => {
          this.store.characters = resp.data;
        }
      ).catch(
        (error) => {
          this.store.characters = [];
        }
      ).finally(
        () => {
          this.store.loading = false;
        }
      );
    },
  },
};
</script>

<template>
  <AppHeader />
  <main>
    <div class="container bg-white">
      <AppSearch @performSearch="getCharacters" />
      <ResultMessage />
      <AppLoader v-if="store.loading" />
      <CharactersList v-else />
    </div>
  </main>
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
.container {
  padding-top: 3rem;
}
</style>