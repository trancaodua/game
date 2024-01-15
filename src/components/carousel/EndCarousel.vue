<template>
    <div class="box-container">
        <div class="title">
            <div class="sub-left-title">
                <i class="title-icon-live"></i>
                <span>LIVE CASINO</span>
            </div>
            <div class="sub-right-title">
                <span>xem thêm</span>
            </div>
        </div>
        <div class="mini-carousel">
            <div :style="{ transform: transform }" ref="miniImgs" class="mini-carousel-container"
                id="mini-carousel-container-two">
                <div v-for="item in data" :key="item.key" class="mini-carousel-item-container-two">
                    <div class="mini-carousel-item-two">
                        <div class="mini-carousel-tag-hot"></div>
                        <div class="mini-carousel-body-two">
                            <div class="mini-carousel-debet-two">
                                Phí hoàn tối đa <span>1.8</span>
                            </div>
                        </div>
                    </div>
                    <div class="mini-carousel-item-two change-postion">
                        <div class="mini-carousel-tag-hot"></div>
                        <div class="mini-carousel-body-two">
                            <div class="mini-carousel-debet-two">
                                Phí hoàn tối đa <span>1.8</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div @click="prev" class="mini-carousel-button left" id="leftTwo"></div>
            <div @click="next" class="mini-carousel-button right" id="rightTwo"></div>
        </div>
    </div>
</template>

<script>
import { ref } from 'vue'

export default {
    setup() {

        const data = [
            {
                key: 0,
                class: "one"
            },
            {
                key: 1,
                class: "two"
            },
        ]

        const miniImgs = ref(null);
        let miniIdx = ref(0);
        let transform = ref("translateX(0)");

        // expose to template and other options API hooks
        return {
            data,
            miniImgs,
            miniIdx,
            transform
        }
    },

    mounted() {
    },
    methods: {
        miniRun() {
            this.miniIdx++;
            this.miniChangeImage();
        },
        miniChangeImage() {
            if (this.miniIdx > this.data.length - 1) {
                this.miniIdx = 0;
            }
            else if (this.miniIdx < 0) {
                this.miniIdx = this.data.length - 1;
            }
            this.transform = `translateX(${-this.miniIdx * this.miniImgs.offsetWidth}px)`;
        },
        next() {
            console.log(this.miniIdx);
            this.miniIdx++;
            this.miniChangeImage();
        },
        prev() {
            this.miniIdx--;
            this.miniChangeImage();
        }
    }
}
</script>
  
<style scoped>
.title {
    margin-top: 0.6em;
    margin-bottom: 0.6em;
    padding: 0 1em;
    color: #5c5c5c;
    font-weight: 500;
    font-size: 1.2em;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
}

.sub-left-title {
    display: flex;
    align-items: center;
}

.title-icon-cp {
    background-position: -0.07em -0.07em;
    margin-right: 0.55em;
    margin-left: 0.3em;
    width: 1.3em;
    height: 1.3em;
    background-image: url(https://www.123bcc.com/home/static-game/img/icon_sprites_lobby.323f0720.png);
    background-position: 0 -0.08em;
    background-size: auto 1.45em;
    display: block;
}

.sub-right-title {
    font-size: 0.75em;
    font-weight: 400;
    padding-right: 1.2em;
    padding-top: 0.5em;
    position: relative;
}

.sub-right-title::after {
    content: "";
    display: block;
    width: 0.9em;
    height: 0.9em;
    background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAUCAYAAACNiR0NAAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAFKADAAQAAAABAAAAFAAAAACy3fD9AAAC+0lEQVQ4Ec1UTUhUURQ+974ZZ0T8eTNgVLugRYsWRSItEqKiMMJwpqRUoh8YVHR0RFtJLgIj0BEXGkVlQeqoM1IQ0cKgTS2CIhSKCgpSIah55ljjz/Pezpnxvp7T1LoDb8553znnu987994B+N+NKYGnehc3LYvlVwBsIhbyNCicvK8n/kQCuHMd+pF7TWzBnsuMuQXkijVkzwcp6yvD8XYLx4DIEN+bNI2hTil/99iL1mMrORwo+MqA1wBjkgno8nXHy1W95uTViH9D0qPTPUaXwrN5i5CS4yH9PmPQIQFVMDlcFU7sIHyssegjZ8yP4zAFyHZ/OF5NeDazZmhP4swiUsqTSP7e5dZKh+qLDMr7wvE6KWQ/Ni05NEdZpLnwhb2P4g0KVdKbp5/FT3wpJWxfSq5FToxKjXLRFs8AY+wazdQU5kRN+Mdm1aN8VsLrAfYzxyWPA4MvWHhIzMS7VQMu1oSLPcXFtibl0kRjn3SpHPmshJQYafB+5hpUMmAr2Bz0hY1zhONiq648hx9JPyFeOmcaNwhX9ldCKhgPep8BZ3WpYiEHfH3GLopTJ4JDBc54EWddi7O1zu0/CalZOmESXQJ3PgdMWUoYGd+iv0WFb1IvAvalPOEqyOZP98/rsCIeYS4fd3YS53eT6lAVEzPGbQxL8JlzumUb4WSp3UuHG39p2PPLyYeI7sGdnXI7PYcHG1iSqqaLgleQlEaRcAI/GAl63hFOllUhKZg1jUH8zDKc06zb4S5Xd3j9LF7ERVY1TfNFWvXXaar0b1aF04XBq/hdASRbwCtzYKS54AOV44E/hu4OPhw4vxBt0WOE2+0PhbRjqLCNFDBNqxwLeaaooar3ewkqHsGcxhi/FGvRB+1EKt5w9fw9RgU2xOguo4Qz4636XSr0hee3SbH2HMNibLgVbfWeVwSZ3lJYO5AoFiCGiAwY71BkqQYhRtNk7PHO3Z5AJon93aFeTC7xjwRm8GY8iIb0ywonj3d3Fl2cu3V/535m2nOZ8S9QDB5yYzxDrwAAAABJRU5ErkJggg==);
    background-size: cover;
    position: absolute;
    right: 0.2em;
    top: 0.5em;
}

.title-icon-mini {
    background-image: url(https://www.123bcc.com/home/static-game/img/mini_sprites.21b0e003.png);
    margin-right: 0.55em;
    margin-left: 0.3em;
    width: 1.3em;
    height: 1.3em;
    background-size: auto 2.05501rem;
    background-position: -4.38402rem -0.274rem;
}

.title-icon-sp {
    background-image: url(https://www.123bcc.com/home/static-game/img/icon_sprites_lobby.323f0720.png);
    margin-right: 0.55em;
    margin-left: 0.3em;
    width: 1.3em;
    height: 1.3em;
    background-position: -10.2em -0.07em;
    background-size: auto 1.45em;
}

.title-icon-live {
    background-image: url(https://www.123bcc.com/home/static-game/img/icon_sprites_lobby.323f0720.png);
    margin-right: 0.55em;
    margin-left: 0.3em;
    width: 1.3em;
    height: 1.3em;
    background-position: -8.76em -0.07em;
    background-size: auto 1.45em;
}

.mini-carousel {
    width: 100%;
    height: 155px;
    overflow: hidden;
    position: relative;
    padding: 0 15px;
}

.mini-carousel-container {
    display: flex;
    transform: translateX(0);
    transition: transform 0.5s ease-in-out;
    width: 100%;
    height: 100%;
}

.mini-carousel-item-container {
    width: 100%;
    height: 100%;
    flex-shrink: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    padding: 0 15px;
}

.mini-carousel-item {
    width: 100%;
    height: 100%;
    position: relative;
    border-radius: 8px;
    max-width: 393px;
    background-repeat: no-repeat;
    background-size: 24.863em auto;
    background-image: url(https://www.123bcc.com/home/static-game/img/sp_sprites.68237151.png);
    background-repeat: no-repeat;
    background-size: 24.863em auto;
}

.mini-carousel-item.two {
    background-position: -0.142em -59.984em;
}

.mini-carousel-item.three {
    background-position: -0.142em -40.037em;
}

.mini-carousel-item.four {
    background-position: -0.142em -20.09em;
}

.mini-carousel-tag-hot {
    width: 2.425em;
    height: 2.425em;
    background: url(data:image/png;base64,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) no-repeat 0 0;
    background-size: 100%;
    position: absolute;
    right: 0;
    top: 0;
    z-index: 91;
}

.mini-carousel-body {
    text-align: center;
    width: 15.33333em;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-end;
    position: absolute;
    right: 0;
}

.mini-carousel-debet {
    font-size: 0.855em;
    font-weight: 500;
    color: #fff;
    line-height: 1.167;
}

.mini-carousel-debet span {
    font-size: 1.167em;
}

.mini-carousel-button-bet {
    display: inline-block;
    width: 6em;
    height: 1.692em;
    background: #ffa240;
    box-shadow: 0 1px 2px 0 rgba(12, 33, 89, 0.28);
    border-radius: 0.784em;
    font-size: 0.926em;
    font-weight: 400;
    color: #fff;
    line-height: 1.692;
    text-align: center;
    margin-top: 1.077em;
    margin-bottom: 1.8464em;
}

.mini-carousel-button {
    position: absolute;
    top: 50%;
    width: 0.8em;
    height: 0.8em;
    background-size: cover;
    background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAGKADAAQAAAABAAAAGAAAAADiNXWtAAABeElEQVRIDdWVvUvEMBiHL7VQi4OKk4N/guDoVOQKbd0dFcRbbnRwc3NxFCfdxUln7YdY6XSTCK5uDk6OUoq19ZeDQC42Nb12uUBI8iZ5nryBtL3erBdSlYDv+zEhZEnX9YFt289Va1RjmmThVlmWG3mej4IgOEZ/TrLu37Asg5LfiWxGkOx5nvfGx1X6sgwm9gK+CclLGIbDiQmFgZKAciBZKIriAld2lyTJqgJ7vERZwIAQbadp+grRDovVtY0FFAbJCuoNJFdRFC12LmBASHZxbTSbPouJ7VQZ8BBI1jB+gOQsjuN5fo72WwsoBBKCephl2SMd86UTAQ8U+50I8Ebowzw3DKMvCnQx0HQM+Dv27OOV/7keymqVAeDXmqatu65bCaeCqTIA+BN7hwDfUkhdaSwA/N40zYFlWR91YDanLAD4C/XIcZxLtlmlVRIAPP5c40oaf65rBQB/45QnOPUp+j8qJxbXyARPAC7jl3nQ9pcpCmdv/AtvVHuBSyIg/QAAAABJRU5ErkJggg==);
}

.mini-carousel-button.left {
    left: 0;
    transform: rotate(180deg);
}

.mini-carousel-button.right {
    right: 0;
}

.mini-carousel-item-container-two {
    width: 100%;
    height: 100%;
    flex-shrink: 0;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    flex-direction: row;
    padding: 0 15px;
    gap: 2px;
}

.mini-carousel-item-two {
    width: 11em;
    height: 9em;
    overflow: hidden;
    position: relative;
    padding: 0 15px;
    background-image: url(https://www.123bcc.com/home/static-game/img/live_sprites.7cf4edaf.png);
    background-repeat: no-repeat;
    background-size: cover;
    flex-shrink: 0;
}

.mini-carousel-body-two {
    text-align: center;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-end;
    position: absolute;
    right: 0;
}

.mini-carousel-debet-two {
    font-size: 0.855em;
    font-weight: 500;
    color: #fff;
    line-height: 1.167;
    margin-bottom: 0.833em;
}

.change-postion {
    background-position: -0.142em -26.8em;
}

@media screen and (max-width: 600px) {

    .mini-carousel-item-two {
        width: 10em;
        height: 8em;
    }

    .change-postion {
        background-position: -0.142em -24.3em;
    }

}
</style>
  