<template>
    <div class="margin-top-30">
        <h5>Titolo: <strong>{{film.title}}</strong></h5>
        <h5>Titolo Originale: <strong>{{film.original_title}}</strong></h5>
        <h6>Lingua: {{film.original_language}}</h6>
        <h6>Voto: {{film.vote_average}}</h6>
        <hr>
    </div>
</template>

<script>
export default {
    name: 'FilmCard',
    props: ['film']
}
</script>

<style lang="scss" scoped>
.margin-top-30{
    margin-top: 30px;
}
</style>