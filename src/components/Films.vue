<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col">
                    <FilmCard v-for="(film, index) in totalList" :key="index" :film="film"/>
                </div>
            </div>
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

</style>