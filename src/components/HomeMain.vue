<script setup>
import HaderCarousel from './carousel/HeaderCarousel.vue';
import BroadCast from './BroadCast.vue';
import GameMenu from './GameMenu.vue';
import MiddleCarousel from './carousel/MiddleCarousel.vue';
import MiniCarousel from './carousel/MiniCarousel.vue';
import MainCarousel from './carousel/MainCarousel.vue';
import EndCarousel from './carousel/EndCarousel.vue';
import AboutMenu from './AboutMenu.vue';
</script>


<template>
    <div class="main">
        <HaderCarousel />
        <BroadCast />
        <GameMenu />
        <MiddleCarousel />
        <MiniCarousel />
        <MainCarousel />
        <EndCarousel />
        <AboutMenu/>
    </div>
</template>
  
<style scoped>
/* Main */
.main {
    flex-grow: 1;
    flex-shrink: 1;
    overflow: auto;
    min-width: 420px;
}
/* End Main */
</style>
  