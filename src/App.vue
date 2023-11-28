<script >
import axios from "axios";
import { store } from "./store";
import AppHeader from './components/AppHeader.vue';
import CharactersList from "./components/CharactersList.vue";
import AppLoader from "./components/AppLoader.vue";
import AppSearch from "./components/AppSearch.vue";

export default {
   data() {
    return {
      store,
    };
  },
  created() {
    this.store.loading = true;
    axios.get(this.store.apiUrl).then((resp) => {
      this.store.characters = resp.data.data;
    }).finally(() => {
            this.store.loading = false;
            console.log(this.store.loading);
        });
  },
  components: {
    AppHeader,
    CharactersList,
    AppLoader,
    AppSearch
  }
}

</script>

<template>
  <AppHeader/>
  <AppSearch/>
  <AppLoader v-if="store.loading" />
  <CharactersList v-else/>
</template>

<style lang="scss">
  @use "./style/general.scss"

</style>
