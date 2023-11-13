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
    <div class="star-ratings">
      <template v-for="i in Math.floor(movie.vote_average / 2)">
        <i class="fas fa-star"></i>
      </template>
      <template v-if="movie.vote_average % 2 !== 0">
        <i class="fas fa-star-half"></i>
      </template>
    </div>
  </div>
</template>

<style lang="scss">
@import url("https://cdn.jsdelivr.net/npm/flag-icon-css@3.5.0/css/flag-icon.min.css");
@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css");
.card__film {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 10px;
}

.star-ratings {
    color: rgb(251, 255, 0);
  }
</style>
