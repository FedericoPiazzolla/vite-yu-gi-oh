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
    background-color: $main-bg-color;
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
      }

      p {
        color: black;
      }
    }
    
  }
</style>