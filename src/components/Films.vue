<template>
<div>
    <div v-if="totalList.length==0">
        <div class="container">
            <div class="row">
                <!-- Trailer La casa di carta  -->
                <div class="youtube">
                    <iframe width="560" height="315" src="https://www.youtube.com/embed/XYWnzNwHF0E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                    <div class="casa-carta">
                        <div class="trailer">
                            <div class="trailer-image">
                                <img src="https://occ-0-2794-2219.1.nflxso.net/dnm/api/v6/tx1O544a9T7n8Z_G12qaboulQQE/AAAABcqprX8EYukOIdx7s-5jXL-C0yhKm7klDENKt3kpev1Z886NDG-S7YmcQti2t7z7QvXynwEwlbNaMuhOQeBlZO9wqDN-10P1JABDekpFX64vLYMPH9kmhXz8nkUy-m4njpjm1rg5Kfyqsq4_M8ePNDULAihVxfcnnF2NcIF2ihC4XA.png?r=c95" alt="">
                            </div>
                            <p>Otto ladri si barricano nell'edificio della Zecca spagnola con alcuni ostaggi, mentre una mente criminale manipola la polizia per mettere in atto il suo piano.</p>
                        </div>
                    </div>
                </div>
                
                <h4 class="margin-top-20">Popolari su Boolflix</h4>
                <!-- sezione Homepage con i film più popolari  -->
                <div class="col col-sm-12 col-md-6 col-lg-4 d-flex align-self-start" v-for="(movie, index) in moviesHomePage" :key="index">
                    <div class="film-card">
                        <div class="card-image">
                            <img :src="`https://image.tmdb.org/t/p/w342/` + movie.poster_path" :alt="movie.original_title">
                        </div>
                        <div class="info">
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
            moviesHomePage: []
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

.youtube {
    position: relative;
}
iframe {
    width: 100%;
    height: 400px;
}
.trailer {
    position: absolute;
    left: 50px;
    bottom: 50px;
    width: 50%;
    color: $mainColor;
    margin: 10px 0;
   .trailer-image {
       max-width: 350px;
       margin-bottom: 10px;
       img {
           width: 100%;
       }
   }
}

h4 {
    color: #A7A7A7;
}
.margin-top-20 {
    margin-top: 20px;
}
</style>