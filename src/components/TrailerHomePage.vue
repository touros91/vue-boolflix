<template>
<div class="youtube">
    <!-- Trailer La casa di carta  -->
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
</template>

<script>
export default {
    name: 'TrailerHomePage'
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
    left: 40px;
    bottom: 80px;
    width: 50%;
    color: rgb(219, 217, 217);
    margin: 10px 0;
   .trailer-image {
       max-width: 350px;
       margin-bottom: 10px;
       img {
           width: 100%;
       }
   }
}
</style>