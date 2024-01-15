<script setup>
import HaderCarousel from './carousel/HeaderCarousel.vue';
import BroadCast from './BroadCast.vue';
import GameMenu from './GameMenu.vue';
import MiddleCarousel from './carousel/MiddleCarousel.vue';
import MiniCarousel from './carousel/MiniCarousel.vue';
import MainCarousel from './carousel/MainCarousel.vue';
import EndCarousel from './carousel/EndCarousel.vue';
import AboutMenu from './AboutMenu.vue';
</script >


<template>
    <div class="main">
        <HaderCarousel />
        <BroadCast />
        <GameMenu />
        <MiddleCarousel />
        <MiniCarousel />
        <MainCarousel :gameType="gameTypeOne" />
        <EndCarousel />
        <MainCarousel :gameType="gameTypeTwo" />
        <MainCarousel :gameType="gameTypeThree" />
        <MainCarousel :gameType="gameTypeFour" />
        <AboutMenu />
    </div>
</template>

<script>
import { ref } from 'vue'

export default {
    data() {
        return {
            gameTypeOne: { name: "TRẬN CẦU ĐỈNH CAO", image: "https://www.123bcc.com/home/static-game/img/sp_sprites.68237151.png", backgroundPosition: "-10.2em -0.07em" },
            gameTypeTwo: { name: "BẮN CÁ", image: "https://www.123bcc.com/home/static-game/img/by_sprites.cc180269.png", backgroundPosition: "-3em -0.07em" },
            gameTypeThree: { name: "ĐÁ GÀ", image: "https://www.123bcc.com/home/static-game/img/dj_sprites.5318b20c.png", backgroundPosition: "10.2em -0.07em" },
            gameTypeFour: { name: "GAME BÀI", image: "https://www.123bcc.com/home/static-game/img/qp_css_sprites.0d56dc9b.png", backgroundPosition: "-3em -0.07em" },
        };
    }
}
</script>
  
<style scoped>
/* Main */
.main {
    flex-grow: 1;
    flex-shrink: 1;
    overflow: auto;
}

/* End Main */
</style>
  