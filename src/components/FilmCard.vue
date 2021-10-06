<template>
    <div class="margin-top-30">
        <div class="films" v-if="film.title != null">
            <h5>Titolo Film: <strong>{{film.title}}</strong></h5>
            <h5>Titolo Film Originale: <strong>{{film.original_title}}</strong></h5>
            <h6>Lingua: {{film.original_language.toUpperCase()}} <lang-flag :iso='film.original_language' :squared="false"/></h6>
            <h6>Voto: {{film.vote_average}}</h6>
            <img :src="`https://image.tmdb.org/t/p/w154/` + film.poster_path" :alt="film.original_title">
            <hr>
        </div>
        <div class="series" v-if="film.name != null">
            <h5>Titolo Serie TV: <strong>{{film.name}}</strong></h5>
            <h5>Titolo Serie TV Originale: <strong>{{film.original_name}}</strong></h5>
            <h6>Lingua: {{film.original_language.toUpperCase()}} <lang-flag :iso='film.original_language' :squared="false"/></h6>
            <h6>Voto: {{film.vote_average}}</h6>
            <img :src="`https://image.tmdb.org/t/p/w154/` + film.poster_path" :alt="film.name">
            <hr>
        </div>
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