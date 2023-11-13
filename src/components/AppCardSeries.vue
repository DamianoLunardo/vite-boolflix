<script>
export default {
  props: {

    serie: Object,
  },
  computed: {
flagClassTv() {
      const language = this.serie.original_language;
      return `flag-icon flag-icon-${language}`;
    },
  },
};
</script>

<template>
  <div class="card__serie">
    <div>
      <img :src="`https://image.tmdb.org/t/p/w342/${serie.backdrop_path}`" />
    </div>
    <div>{{ serie.original_name }}</div>
    <div>{{ serie.origin_country }}</div>
    <div :class="flagClassTv"></div>
    </div>
</template>

<style lang="scss">
@import url("https://cdn.jsdelivr.net/npm/flag-icon-css@3.5.0/css/flag-icon.min.css");

.card__serie {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 10px;
}
</style>