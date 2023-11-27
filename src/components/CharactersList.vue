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

<div class="my_container container my-5">
  <div class="row">
    <div 
    class="my_col-2 col-2 d-flex gy-3"
    v-for="character in store.characters">
      <AppCard class="w-100" :character="character"/>
    </div>
  </div>
</div>

</template>

<style lang="scss" scoped>
.my_container {
  padding: 2rem;
  background-color: white;

  .my_col-2 {
    width: calc(100% / 5) !important;
  }
}
</style>