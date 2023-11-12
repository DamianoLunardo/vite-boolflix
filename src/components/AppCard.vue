<script>
export default {
  props: {
    movie: Object,
  },
};


</script>

<template>
    <div class="card__film">
      <div>{{ movie.title }}</div>
      <div>{{ movie.original_title }}</div>
      <div>{{ movie.original_language }}</div>
      <div>{{ movie.vote_average }}</div>
    </div>
  </template>

<style lang="scss">
.card__film {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 10px;
}

</style>