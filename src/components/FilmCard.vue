<template>
    <div class="col col-sm-12 col-md-6 col-lg-4 d-flex align-self-start">
        <!-- contenitore Films  -->
        <div class="film-card" v-if="film.title">
            <div class="card-image">
                <img v-if="film.poster_path" :src="`https://image.tmdb.org/t/p/w342/` + film.poster_path" :alt="film.original_title">
                <img v-else :src="this.alternativeImage" :alt="altText">
            </div>
            <div class="info">
                <h5>Titolo Film: <strong>{{film.title}}</strong></h5>
                <h5>Titolo Film Originale: <strong>{{film.original_title}}</strong></h5>
                <h6>Lingua: {{film.original_language.toUpperCase()}} <lang-flag :iso='film.original_language' :squared="false"/></h6>
                <h6>Voto: {{Math.round(film.vote_average/2)}} 
                    <i class="fas fa-star yellow" v-for="(star, index) in Math.round(film.vote_average/2)" :key="index"></i>
                    <i class="far fa-star" v-for="(starEmpty, index) in (5 - Math.round(film.vote_average/2))" :key="index"></i>
                </h6>
                <div><strong>Overview: </strong>{{film.overview}}</div>
            </div>
        </div>
        <!-- contenitore Serie TV          -->
        <div class="serie-card" v-if="film.name"> 
            <div class="card-image">
                <img v-if="film.poster_path" :src="`https://image.tmdb.org/t/p/w342/` + film.poster_path" :alt="film.original_title">
                <img v-else :src="this.alternativeImage" :alt="altText">
            </div>
            <div class="info">
                <h5>Titolo Serie TV: <strong>{{film.name}}</strong></h5>
                <h5>Titolo Serie TV Originale: <strong>{{film.original_name}}</strong></h5>
                <h6>Lingua: {{film.original_language.toUpperCase()}} <lang-flag :iso='film.original_language' :squared="false"/></h6>
                <h6>Voto: {{Math.round(film.vote_average/2)}}
                    <i class="fas fa-star yellow" v-for="(star, i) in Math.round(film.vote_average/2)" :key="i"></i>
                    <i class="far fa-star" v-for="(starEmpty, index) in (5 - Math.round(film.vote_average/2))" :key="index"></i>
                </h6>
                <div><strong>Overview: </strong>{{film.overview}}</div>
            </div>
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
    },
    data() {
        return {
            alternativeImage: 'https://hd2.tudocdn.net/815221?w=1200&h=900',
            altText: 'Netflix'
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common.scss';
@import '../assets/style/commonCardStyle.scss';
</style>