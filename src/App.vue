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
        // metodo che registra l'evento $emit inviato dal figlio Header nel padre App e che effettua una chiamata Axios per i films e una chiamata Axios per le serie tv
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
            });   
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: paramsObj
            })
            .then((resp) => {
                this.series = resp.data.results;
            });  
        }
    },
    computed: {
        // computed property che concatena gli array films e serie in un terzo array per la visualizzazione nella homepage 
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
