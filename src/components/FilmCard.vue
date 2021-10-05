<template>
    <div >
        <div>Titolo: {{film.titolo}}</div>
        <div>Titolo Originale: {{film.titoloOriginale}}</div>
        <div>Lingua: {{film.lingua}}</div>
        <div>Voto: {{film.voto}}</div>
        <hr>
    </div>
</template>

<script>
export default {
    name: 'FilmCard',
    props: ['film']
}
</script>

<style>

</style>