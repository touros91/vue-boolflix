<template>
  <div id="app">
    <Header @search="searchFilm"/>
    <main>
      <Films :movieList="movies"/>
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
            movies: []
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
                  .then((resp)=>{
                      this.movies = resp.data.results;
                  });   
          }
    }
}
</script>

<style lang="scss">
@import './assets/style/common.scss'
</style>
