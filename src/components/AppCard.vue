<script>
export default {
  props: {
    movie: Object,
  },
  computed: {
    flagClass() {
      const languageCode = this.movie.original_language;
      return `flag-icon flag-icon-${languageCode}`;
    },
  },
};
</script>

<template>
  <div class="card__film">
    <div>
      <img :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" />
    </div>
    <div>{{ movie.title }}</div>
    <div>{{ movie.original_title }}</div>
    <div :class="flagClass"></div>
    <div>{{ movie.vote_average }}</div>
  </div>
</template>

<style lang="scss">
@import url("https://cdn.jsdelivr.net/npm/flag-icon-css@3.5.0/css/flag-icon.min.css");
.card__film {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 10px;
}
</style>
