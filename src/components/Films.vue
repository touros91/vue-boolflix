<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col p-3">
                    <FilmCard v-for="(film, index) in moviesResult" :key="index" :film="film"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import FilmCard from './FilmCard.vue';

export default {
    name: 'Films',
    props: ['moviesResult'],
    components: {
        FilmCard
    },
    data(){
        return {
            movies: []
        }
    },
    // methods: {
    //     findFilm(){
    //         axios.get('https://api.themoviedb.org/3/search/movie',{
    //             params: {
    //                 api_key: 'dfb070b958255d617f646fa427b32530',
    //                 query: this.film,
    //                 language: 'it-IT'
    //             }
    //         })
    //         .then((resp)=>{
    //             this.movies = resp.data.results;
    //         });   
    //     }
    // },
    // computed: {
    //     movieList(){
    //         const filmList = []
    //         this.movies.forEach(
    //             (elm) => {
    //                     filmList.push(
    //                         {
    //                             titolo: elm.title,
    //                             titoloOriginale: elm.original_title,
    //                             lingua: elm.original_language,
    //                             voto: elm.vote_average
    //                         }
    //                     );  
    //             }
    //         );
    //         return filmList;
    //     }
    // }
    
     
}
</script>

<style>

</style>