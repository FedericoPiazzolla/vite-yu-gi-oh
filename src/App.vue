<script >
import axios from "axios";
import { store } from "./store.js";
import AppHeader from './components/AppHeader.vue';
import CharactersList from "./components/CharactersList.vue";

export default {
   data() {
    return {
      store
    };
  },
  created() {
    axios
      .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
      .then((resp) => {
        this.store.characters = resp.data.data;
      });
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
