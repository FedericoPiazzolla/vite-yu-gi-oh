<script>
import { store } from '../store';

export default {
  data() {
    return {
      store,
    }
  }
};
</script>

<template>
  <div class="container mt-5">
    <select 
    name="chose-archetype" 
    id="chose-archetype"
    v-model="store.searchText"
    @change="$emit(`search`)"
    >
      <option v-for="archetype in store.archetypeArray" :value="`${archetype}`">{{ archetype }}</option>
    </select>
  </div>
</template>

<style lang="scss" scoped>

  #chose-archetype {
    width: 20%;
    padding: .5rem;
  }
</style>