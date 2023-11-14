<script>
import AppCard from "./AppCard.vue";
import axios from "axios";
import { store } from "../store";

export default {
    components: {
        AppCard,
    },
    data() {
        return {
            store,
            movies: [],
            series: [],
        };
    },
    methods: {
        fetchMovies() {
            axios
                .get("https://api.themoviedb.org/3/search/movie", {
                    params: {
                        api_key: this.store.API_KEY,
                        query: this.store.query,
                    },
                })
                .then((res) => {
                    this.movies = res.data.results;
                    console.log(res.data.results);
                });
        },
        fetchSeries() {
            axios
                .get("https://api.themoviedb.org/3/search/tv", {
                    params: {
                        api_key: this.store.API_KEY,
                        query: this.store.query,
                    },
                })
                .then((res) => {
                    this.series = res.data.results;
                    console.log(res.data.results);
                });
        },
    },

    watch: {
        "store.query": function () {
            this.fetchMovies();
            this.fetchSeries();
        },
    },
};
</script>

<template>
    <h3 v-if="movies.length> 0" class="info-text">I film trovati sono:</h3>
    <div class="card-grid">
        <AppCard v-for="movie in movies" :key="movie.id" :movie="movie" />
    </div>
    <h3 v-if="series.length > 0" class="info-text">Le serie trovate sono:</h3>
    <div class="card-grid">
        <AppCard v-for="serie in series" :key="serie.id" :serie="serie" />
    </div>
</template>

<style lang="scss">
.card-grid {
    padding-top: 40px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
}

.info-text {
    padding-top: 20px;
}
</style>
