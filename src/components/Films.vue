<template>
<div class="container">
    <div class="row">
        <FilmCard v-for="(film, index) in totalList" :key="index" :film="film"/>
    </div>
</div>
</template>

<script>
import FilmCard from './FilmCard.vue';

export default {
    name: 'Films',
    props: ['totalList'],
    components: {
        FilmCard
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common.scss';
</style>