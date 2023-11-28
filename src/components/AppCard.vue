<script>
export default {
  props: {
    character: Object,
  },
};
</script>

<template>
  <div class="text-center my_card h-100">
    <img :src="character.card_images[0].image_url" :alt="character.name">
    <div class="my_info_card">
      <h4 class="mt-3">{{ character.name }}</h4>
      <p>{{ character.archetype ? character.archetype : "nessun archetipo" }}</p>
    </div>
    
  </div>
</template>

<style lang="scss" scoped>
@use "../style/partials/variable" as *;
  .my_card {
    // background-color: $main-bg-color;
    background-image: url(../assets/img/background-yu-gi-oh.png);
    border: 3px solid black;
    color: white;

    img {
      max-width: 100%;
    }

    .my_info_card {
      display: flex;
      flex-direction: column;
      
      h4 {
        font-size: 1rem;
        padding: 1rem;
        font-weight: bold;
      }

      p {
        color: black;
        font-size: .8rem;
        display: inline-block;
        color: yellow;
      }
    }
    
  }
</style>