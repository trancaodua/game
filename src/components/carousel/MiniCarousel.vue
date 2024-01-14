<template>
    <div class="mini-box-container">
        <div class="title">
            <div class="sub-left-title">
                <i class="title-icon-mini"></i>
                <span>TRÒ CHƠI</span>
            </div>
            <div class="sub-right-title">
                <span>xem thêm</span>
            </div>
        </div>
        <div  ref="slider" class="mini-box-content" @mousemove="dragging" @touchmove="dragging" @mousedown="dragStart" @touchstart="dragStart" @mouseup="mouseUp">
            <div ref="innerSlider" class="mini-box-slider">
                <div v-for="item in data" :key="item.key" class="mini-content-container mini-sprites" :class="[item.class]">
                    <div class="mini-box-game-tag"></div>
                    <div class="mini-box-body">
                        <img :src="item.src" />
                    </div>
                    <div class="mini-box-footer">
                        <div>{{ item.name }}</div>
                        <div>60 giây mở thưởng</div>
                    </div>
                </div>
            </div>
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
                src: "https://www.123bcc.com/home/img/cpicon/vn1pfsc.png",
                name: "Bầu Cua",
                class: "mini-sprites"
            },
            {
                key: 1,
                src: "https://www.123bcc.com/home/img/cpicon/vn1pk3.png",
                name: "Tài Xỉu",
                class: "mini-android"
            },
            {
                key: 2,
                src: "https://www.123bcc.com/home/img/cpicon/vn1pk3.png",
                name: "Xóc Đĩa",
                class: "mini-xo-dia"
            },
            {
                key: 3,
                src: "https://www.123bcc.com/home/img/cpicon/vn1pdt.png",
                name: "Rồng Hổ",
                class: "mini-xo-dia"
            },
            {
                key: 4,
                src: "https://www.123bcc.com/home/img/cpicon/vn1pfsc.png",
                name: "Bầu Cua",
                class: "mini-sprites"
            },
            {
                key: 5,
                src: "https://www.123bcc.com/home/img/cpicon/vn1pk3.png",
                name: "Tài Xỉu",
                class: "mini-android"
            },
            {
                key: 6,
                src: "https://www.123bcc.com/home/img/cpicon/vn1pk3.png",
                name: "Xóc Đĩa",
                class: "mini-xo-dia"
            },
            {
                key: 7,
                src: "https://www.123bcc.com/home/img/cpicon/vn1pdt.png",
                name: "Rồng Hổ",
                class: "mini-xo-dia"
            },
        ]
        const pressed = ref(false);
        let startx = 0;;
        const slider = ref(null);
        const innerSlider = ref(null);
        let x = ref(0);

        // expose to template and other options API hooks
        return {
            data,
            pressed,
            startx,
            slider,
            innerSlider,
            x
        }
    },

    mounted() {

    },
    methods: {
        dragStart(e) {
            this.pressed = true;

            let offsetX;
            if (e.targetTouches) {
                let rect = e.target.getBoundingClientRect();
                offsetX = e.targetTouches[0].pageX - rect.left;
            }
            else {
                offsetX = e.offsetX;
            }

            this.startx = offsetX - this.innerSlider.offsetLeft;
            this.slider.style.cursor = "grabbing";
        },
        mouseUp() {
            this.pressed = false;
        },
        dragging(e) {
            if (!this.pressed) return;
            e.preventDefault();

            if (e.targetTouches) {
                let rect = e.target.getBoundingClientRect();
                this.x = e.targetTouches[0].pageX - rect.left;
            }
            else {
                this.x = e.offsetX;
            }

            this.innerSlider.style.left = `${this.x - this.startx}px`;
            this.checkBoundary();
        },
        checkBoundary() {
            let outer = this.slider.getBoundingClientRect();
            let inner = this.innerSlider.getBoundingClientRect();

            if (parseInt(this.innerSlider.style.left) > 0) {
                this.innerSlider.style.left = "0px";
            }

            if (inner.right < outer.right) {
                this.innerSlider.style.left = `-${inner.width - outer.width}px`;
            }
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

.mini-box-content {
    cursor: grab;
    overflow: hidden;
    position: relative;
    height: 8.49403rem;
    margin: 0 15px;
}

.mini-box-slider {
    height: 100%;
    display: grid;
    grid-template-columns: repeat(8, 1fr);
    gap: 5px;
    pointer-events: none;
    position: absolute;
    top: 0;
}

.mini-content-container {
    width: 8.49403rem;
    height: 8.49403rem;
    position: relative;
}

.mini-sprites {
    background-image: url(https://www.123bcc.com/home/static-game/img/mini_bg_sprites.b05f9dc9.png);
    background-position: -8.69954rem -0.0685rem;
    background-repeat: no-repeat;
    background-size: auto 8.63104rem;
}

.mini-android {
    background-image: url(https://www.123bcc.com/home/static-game/img/mini_bg_sprites.b05f9dc9.png);
    background-position: -17.33057rem -0.0685rem;
    background-repeat: no-repeat;
    background-size: auto 8.63104rem;
}

.mini-xo-dia {
    background-image: url(https://www.123bcc.com/home/static-game/img/mini_bg_sprites.b05f9dc9.png);
    background-position: -0.0685rem -0.0685rem;
    background-repeat: no-repeat;
    background-size: auto 8.63104rem;
}

.mini-box-game-tag {
    width: 2.425em;
    height: 2.425em;
    background: url(data:image/png;base64,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) no-repeat 0 0;
    background-size: 100%;
    position: absolute;
    right: 0;
    top: 0;
}

.mini-box-body {
    margin-bottom: 0.411rem;
    display: flex;
    justify-content: center;
}

.mini-box-footer {
    padding-left: 0.548rem;
    font-size: 0.822rem;
}

.mini-box-body img {
    margin: 0.6165rem auto 0;
    width: 5.00052rem;
    height: 5.00052rem;
}
</style>
  