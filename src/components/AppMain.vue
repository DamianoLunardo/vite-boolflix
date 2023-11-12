<script>
import AppCard from './AppCard.vue';
import AppCardSeries from './AppCardSeries.vue';
import axios from 'axios';
import { store } from '../store';


export default {
    components: {
        
        AppCard,
        AppCardSeries
    },
    data() {
        return {
            store,
            movies: [],
        }
    },
   methods: {
    fetchMovies() {
        axios.get ('https://api.themoviedb.org/3/search/movie',{
            params: {
                api_key: this.store.API_KEY,
                query: this.store.query
            }
        }).then (res => {
            this.movies = res.data.results
            console.log(res.data.results)
        })
    }
   },
    searchMovies() {
        this.fetchMovies();
    },
    watch: {
      'store.query': 'fetchMovies'
    },
}
</script>

<template>
    <AppCard v-for="movie in movies" :key="movie.id" :movie="movie"/>
    <AppCardSeries />
</template>

<style lang="scss">
</style>