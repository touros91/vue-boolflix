<template>
  <div id="app">
    <Header/>
    <main>
      <Films/>
    </main>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Films from './components/Films.vue';


export default {
  name: 'App',
  components: {
    Header,
    Films
  }
}
</script>

<style lang="scss">
@import './assets/style/common.scss'
</style>
