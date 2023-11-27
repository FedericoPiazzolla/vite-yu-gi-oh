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

<div class="container">
  <div class="row">
    <div 
    class="col"
    v-for="character in store.characters"
    :key="character.id"
    >
    <AppCard/>
    </div>
  </div>
</div>

</template>

<style lang="scss" scoped>
</style>