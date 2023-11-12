<script>
import { store } from '../store';

export default {
  data() {
    return {
      store,
    };
  },
  methods: {
  
    searchMovies() {
      this.$emit('searchMovies'); 
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="header">
      <div>Qui ci va il logo (Parte destra)</div>
      <div>
        <input v-model="store.query" type="text" placeholder="Cerca..." />
        <button @click="searchMovies">Cerca</button>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.header {
  display: flex;
  justify-content: space-between;
}
</style>
