<template>
<div>
    <div v-if="totalList.length==0">
        <div class="container">
            <div class="row">
                <!-- Trailer La casa di carta  -->
                <TrailerHomePage/>
                <h4 class="margin-top-20">Popolari su Boolflix</h4>
                <!-- sezione Homepage con i film più popolari  -->
                <div class="col-12 col-md-6 col-lg-4 d-flex justify-content-center" v-for="(movie, index) in moviesHomePage" :key="index">
                    <div class="film-card">
                        <div class="card-image">
                            <img :src="`https://image.tmdb.org/t/p/w342/` + movie.poster_path" :alt="movie.original_title">
                        </div>
                        <div class="info">
                            <h5>Titolo Film: <strong>{{movie.title}}</strong></h5>
                            <h5>Titolo Film Originale: <strong>{{movie.original_title}}</strong></h5>
                            <h6>Lingua: {{movie.original_language.toUpperCase()}} <lang-flag :iso='movie.original_language' :squared="false"/></h6>
                            <!-- calcolo del voto  -->   
                            <h6>Voto: {{Math.round(movie.vote_average/2)}} 
                                <!-- calcolo e visualizzazione del voto in stelle -->
                                <i class="fas fa-star yellow" v-for="(star, index) in Math.round(movie.vote_average/2)" :key="index"></i>
                                <i class="far fa-star" v-for="(starEmpty, index) in (5 - Math.round(movie.vote_average/2))" :key="index"></i>
                            </h6>
                            <div><strong>Overview: </strong>{{movie.overview}}</div>
                        </div>
                    </div>
                </div>                
            </div>
        </div>
    </div>
    <div class="container">
        <div class="row">
            <FilmCard v-for="(film, index) in totalList" :key="index" :film="film"/>
        </div>
    </div>
</div>
</template>

<script>
import FilmCard from './FilmCard.vue';
import axios from 'axios';
import LangFlag from 'vue-lang-code-flags';
import TrailerHomePage from './TrailerHomePage.vue';

export default {
    name: 'Films',
    props: ['totalList'],
    components: {
        FilmCard,
        LangFlag,
        TrailerHomePage
    },
    data(){
        return{
            apiKey: 'dfb070b958255d617f646fa427b32530',
            moviesHomePage: []
        }
    },
    created (){
        const paramsObj = {
                            api_key: this.apiKey,
                            query: 'you',
                            language: 'it-IT'
                        };
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: paramsObj
            })
            .then((resp) => {
                this.moviesHomePage = resp.data.results;
            });
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common.scss';
@import '../assets/style/commonCardStyle.scss';

h4 {
    color: #A7A7A7;
}
.margin-top-20 {
    margin-top: 20px;
}
</style>