<script >
import axios from "axios";
import { store } from "./store";
import AppHeader from './components/AppHeader.vue';
import CharactersList from "./components/CharactersList.vue";

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
    });
    this.store.loading = false;

  },
  components: {
    AppHeader,
    CharactersList,
  }
}

</script>

<template>
  <AppHeader/>
  <CharactersList />
</template>

<style lang="scss">
  @use "./style/general.scss"

</style>
