<script>
export default {
  props: {
    movie: Object,
    serie: Object,
  },
  data() {
    return {
      showInfo: false,
    };
  },
  computed: {
    flagClass() {
      const languageCode = this.movie.original_language;
      return `flag-icon flag-icon-${languageCode}`;
    },
    flagClassTv() {
      const language = this.serie.original_language;
      return `flag-icon flag-icon-${language}`;
    },
  },
};
</script>

<template>
<div v-if="movie && movie.poster_path" class="card__film" @mouseover="showInfo = true" @mouseleave="showInfo = false">
  <div v-if="movie && movie.poster_path">
    <img :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" />
  </div>
  <div v-if="showInfo" class="film-info">
    <div>{{ movie.title === movie.original_title ? movie.original_name : movie.title }}</div>
    <div>{{ movie.original_title }}</div>
    <div class="overview-text">{{ movie.overview }}</div>
    <div>{{ movie.release_date }}</div>
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
</div>

<div v-if="serie && serie.poster_path" class="card__serie" @mouseover="showInfo = true" @mouseleave="showInfo = false">
  <div v-if="serie && serie.poster_path">
    <img :src="`https://image.tmdb.org/t/p/w342/${serie.poster_path}`" />
  </div>
  <div v-if="showInfo" class="serie-info">
    <div>{{ serie.original_name }}</div>
    <div>{{ serie.origin_country }}</div>
    <div class="overview-text">{{ serie.overview }}</div>
    <div :class="flagClassTv"></div>
    <div>{{ serie.first_air_date }}</div>
    <div class="star-ratings">
      <template v-for="i in Math.floor(serie.vote_average / 2)">
        <i class="fas fa-star"></i>
      </template>
      <template v-if="serie.vote_average % 2 !== 0">
        <i class="fas fa-star-half"></i>
      </template>
    </div>
  </div>
</div>

</template>

<style lang="scss">
@import url("https://cdn.jsdelivr.net/npm/flag-icon-css@3.5.0/css/flag-icon.min.css");
@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css");

.card__film, .card__serie {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 10px;
  position: relative;
}

.film-info, .serie-info {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: black;
  display: flex;
  flex-direction: column;
  padding: 5px;
  gap: 10px;
}

.overview-text {
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 8;
  -webkit-box-orient: vertical;
}

.star-ratings {
  color: rgb(251, 255, 0);
}
</style>
