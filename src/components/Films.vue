<template>
<div>
    <div v-if="totalList.length==0">
        <div class="container">
            <div class="row">
                <div class="col-4 d-flex" v-for="(movie, index) in moviesHomePage" :key="index">
                    <div class="film-card">
                        <div class="card-image" @mouseover="visible=false" @mouseleave="visible=true" v-show="visible">
                            <img :src="`https://image.tmdb.org/t/p/w342/` + movie.poster_path" :alt="movie.original_title">
                        </div>
                        <div class="info" v-show="visible==false">
                            <h5>Titolo Film: <strong>{{movie.title}}</strong></h5>
                            <h5>Titolo Film Originale: <strong>{{movie.original_title}}</strong></h5>
                            <h6>Lingua: {{movie.original_language.toUpperCase()}} <lang-flag :iso='movie.original_language' :squared="false"/></h6>
                            <h6>Voto: {{Math.round(movie.vote_average/2)}} 
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

export default {
    name: 'Films',
    props: ['totalList'],
    components: {
        FilmCard,
        LangFlag
    },
    data(){
        return{
            moviesHomePage: [],
            visible: true
        }
    },
    created (){
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=dfb070b958255d617f646fa427b32530&language=it_IT&query=with')
        .then((resp) => {
            this.moviesHomePage = resp.data.results;
            console.log(this.moviesHomePage);
        });   
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common.scss';
@import '../assets/style/commonCardStyle.scss';
</style>