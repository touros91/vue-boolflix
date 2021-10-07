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
            apiKey: 'dfb070b958255d617f646fa427b32530',
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
            const paramsObj = {
                                api_key: this.apiKey,
                                query: filmToSearch,
                                language: 'it-IT'
                            };
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: paramsObj
            })
            .then((resp) => {
                this.movies = resp.data.results;
                console.log(this.movies);

            });   
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: paramsObj
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
@import './assets/style/commonCardStyle.scss';
</style>
