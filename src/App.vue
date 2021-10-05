<template>
  <div id="app">
    <Header @search="searchFilm"/>
    <main>
      <Films :film="film"/>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Films from './components/Films.vue';

export default {
  name: 'App',
  data(){
    return {
      film: ""
    }
  },
  components: {
    Header,
    Films
  },
  methods: {
    searchFilm(filmToSearch){
      this.film = filmToSearch;
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/common.scss'
</style>
