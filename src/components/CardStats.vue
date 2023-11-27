<script>
import { store } from "../store";
export default {
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div class="container">
    <p class="col-12">Found {{ store.characters.length }} cards</p>
  </div>
</template>

<style lang="scss" scoped>
.container {
  padding: 0;

  p {
    background-color: black;
    color: white;
    padding: 1rem;
  }
  
}
</style>