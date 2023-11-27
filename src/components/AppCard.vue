<script>
export default {
  props: {
    character: Array,
  },
};
</script>

<template>
  <div class="text-center my_card">
    <img :src="character.card_images[0].image_url" alt="">
    <h4>{{ character.name }}</h4>
  </div>
</template>

<style lang="scss" scoped>
@use "../style/partials/variable" as *;
  .my_card {
    background-color: $main-bg-color;
    color: white;

    img {
      max-width: 100%;
    }
  }
</style>