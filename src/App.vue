<script >
import axios from "axios";
import { store } from "./store.js";
import AppHeader from './components/AppHeader.vue';

export default {
   data() {
    return {
      store
    };
  },
  created() {
    axios.get(this.store.apiUrl).then((resp) => {
      this.store.characters = resp.data.result;
    });
  },
  components: {
    AppHeader,
  }
}

</script>

<template>
  <AppHeader/>
</template>

<style lang="scss">
  @use "./style/general.scss"

</style>
