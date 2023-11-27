<script>
import { store } from "../store";
import AppCard from "./AppCard.vue";

  export default {
    data() {
      return {
        store,
      };
    },
    components: {
      AppCard,
    }
  };
</script>

<template>

<div class="container my_container">
  <div class="row">
    <div 
    class="col my_col"
    v-for="character in store.characters">
      <AppCard :character="character"/>
    </div>
  </div>
</div>

</template>

<style lang="scss" scoped>
.my_container {
  padding: 2rem;
  background-color: white;

  .my_col {
    width: calc(100% / 5) !important;
  }
}
</style>