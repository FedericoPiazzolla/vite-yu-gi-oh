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
    setTimeout(() => {
      axios
      .get(this.store.apiUrl)
      .then((resp) => {
        this.store.characters = resp.data.data;
      })
      .finally(this.store.loading = false)
      
    },2000)
    
  },
  components: {
    AppHeader,
    CharactersList,
    AppLoader,
    AppSearch
  },
  methods: {
    apiFocus(num) {

      const params = {
        num: num,
        offset: 0,
      }

      if (this.store.searchText !== "") {
        params.archetype = this.store.searchText;
      }
      axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php", {
          params
        })
        .then((resp) => {
          this.store.characters = resp.data.data;
        })
    },
    selectCards() {
      this.store.indexCard = 0;
      this.apiFocus(100);
    },
  }
};

</script>

<template>
  <AppHeader/>
  <AppSearch @search="selectCards"/>
  <AppLoader v-if="store.loading" />
  <CharactersList v-else/>
</template>

<style lang="scss">
  @use "./style/general.scss"

</style>
