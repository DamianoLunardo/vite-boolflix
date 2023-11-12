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
           // series: [],
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
    },
   // fetchSeries() {
       // axios.get ('https://api.themoviedb.org/3/search/tv',{
          //  params: {
              //  api_key: this.store.API_KEY,
              // query: this.store.query
           // }
       // }) .then (res => {
          //  this.series = res.data.results
         //   console.log(res.data.results)
       // })
    //},
   },
    searchMovies() {
        this.fetchMovies();
    },
    watch: {
      'store.query': 'fetchMovies'
    },
   // searchSeries() {
  //      this.fetchSeries();
  //  },
   // watch: {
     // 'store.query': 'fetchSeries'
   // },
}
</script>

<template>
    <AppCard v-for="movie in movies" :key="movie.id" :movie="movie"/>
  <!-- <AppCardSeries v-for="serie in series" :key="serie.id" :serie="serie"/>-->
</template>

<style lang="scss">
</style>