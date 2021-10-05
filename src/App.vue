<template>
  <div id="app">
    <Header @search="searchFilm"/>
    <main>
      <Films :moviesResult="movieList"/>
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
            film: "",
            movies: []
        }
    },
    components: {
        Header,
        Films
    },
    methods: {
        searchFilm(filmToSearch){
            this.film = filmToSearch;
            axios.get('https://api.themoviedb.org/3/search/movie',{
                      params: {
                          api_key: 'dfb070b958255d617f646fa427b32530',
                          query: this.film,
                          language: 'it-IT'
                      }
                  })
                  .then((resp)=>{
                      this.movies = resp.data.results;
                  });   
          }
    },
    computed: {
        movieList(){
            const filmList = []
            this.movies.forEach(
                (elm) => {
                    filmList.push(
                        {
                          titolo: elm.title,
                          titoloOriginale: elm.original_title,
                          lingua: elm.original_language,
                          voto: elm.vote_average
                        }
                    );  
                }
            );
            return filmList;
        }
    }
}
</script>

<style lang="scss">
@import './assets/style/common.scss'
</style>
