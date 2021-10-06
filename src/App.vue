<template>
  <div id="app">
    <Header @search="searchFilm"/>
    <main>
      <Films :totalList="totalListMovies"/>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Films from './components/Films.vue';
import axios from 'axios';

export default {
    name: 'App',
    data(){
        return {
            movies: [],
            series: [],
        }
    },
    components: {
        Header,
        Films
    },
    methods: {
        searchFilm(filmToSearch){
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: 'dfb070b958255d617f646fa427b32530',
                    query: filmToSearch,
                    language: 'it-IT'
                }
            })
            .then((resp) => {
                this.movies = resp.data.results;
                console.log(this.movies);

            });   
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key: 'dfb070b958255d617f646fa427b32530',
                    query: filmToSearch,
                    language: 'it-IT'
                }
            })
            .then((resp) => {
                this.series = resp.data.results;
                console.log(this.series);
            });  
        }
    },
    computed: {
        totalListMovies(){
            let totalList = [];
            totalList = this.movies.concat(this.series);     
            return totalList;
        }
    }
}
</script>

<style lang="scss">
@import './assets/style/common.scss';
</style>
