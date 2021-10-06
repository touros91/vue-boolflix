<template>
    <div class="margin-top-30">
        <h5>Titolo: <strong>{{film.title}}</strong></h5>
        <h5>Titolo Originale: <strong>{{film.original_title}}</strong></h5>
        <h6>Lingua: <lang-flag :iso='film.original_language' :squared="false"/></h6>
        <h6>Voto: {{film.vote_average}}</h6>
        <hr>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: 'FilmCard',
    props: ['film'],
    components: {
        LangFlag
    }
}
</script>

<style lang="scss" scoped>
.margin-top-30{
    margin-top: 30px;
}
</style>