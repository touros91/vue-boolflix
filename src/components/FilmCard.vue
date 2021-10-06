<template>
    <div class="col-4 d-flex">
        <div class="film-card" v-if="film.title != null">
            <div class="card-image" @mouseover="visible=false" @mouseleave="visible=true" v-show="visible">
                <img :src="`https://image.tmdb.org/t/p/w342/` + film.poster_path" :alt="film.original_title">
            </div>
            <div class="info" v-show="visible==false">
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
        
        <div class="serie-card" v-if="film.name != null"> 
            <div class="card-image" @mouseover="visible=false" @mouseleave="visible=true" v-show="visible">
                <img :src="`https://image.tmdb.org/t/p/w342/` + film.poster_path" :alt="film.original_name">
            </div>
            <div class="info" v-show="visible==false">
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
            visible: true
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common.scss';

.film-card, .serie-card {
    padding: 30px 0;
    margin-bottom: 30px;
}
.info {
    height: 515px;
    background-color: black;
    color: white;
    padding: 20px;
}
.yellow {
    color: rgb(255, 190, 0);
}
</style>