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
            store
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
            console.log(res.data.results)
        })
    }
   },
    created() {
        this.fetchMovies(),
        console.log('Created')
    }
}
</script>

<template>
    <AppCard />
    <AppCardSeries />
</template>

<style lang="scss">
</style>