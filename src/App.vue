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
      axios.get(this.store.apiUrl).then((resp) => {
        this.store.characters = resp.data.data;
      })
      this.store.loading = false;
    },2000)
    
  },
  components: {
    AppHeader,
    CharactersList,
    AppLoader,
    AppSearch
  },
  methods: {
    apiFocus(num, offset, archetype) {
      axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php", {
          params: {
            num: num,
            offset: offset,
            archetype: archetype,
          }
        })
        .then((resp) => {
          this.store.characters = resp.data.data;
        })
    },
    selectCards() {
      this.store.indexCard = 0;
      this.apiFocus(20, 0, this.store.searchText);
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
