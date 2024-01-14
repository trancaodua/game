<template>
    <div class="box-container">
        <div class="title">
            <div class="sub-left-title">
                <i class="title-icon-cp"></i>
                <span>KẾT QUẢ XỔ SỐ</span>
            </div>
            <div class="sub-right-title">
                <span>xem thêm</span>
            </div>
        </div>
        <div ref="slider" class="box-content" @mousemove="dragging" @touchmove="dragging" @mousedown="dragStart"
            @touchstart="dragStart" @mouseup="mouseUp">
            <div ref="innerSlider" class="box-slider">
                <div class="content-container" v-for="item in data" :key="item.key" draggable="false">
                    <div class="content-header">
                        <span>{{ item.name }}</span>
                        <span>10/01/2024</span>
                    </div>
                    <div class="content-body">
                        <span>1</span>
                        <span>2</span>
                        <span>3</span>
                        <span>4</span>
                        <span>5</span>
                    </div>
                    <div class="content-footer">
                        <span>14/01/2024</span>
                        <span>18:49:51</span>
                        <button>Cược ngay</button>
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
                name: "Khánh Hòa"
            },
            {
                key: 1,
                src: "Miền Bắc"
            },
            {
                key: 2,
                src: "Long An"
            },
            {
                key: 3,
                src: "Cà Mau"
            }
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

/* .box-container {
  margin: 0 15px;
} */
.box-content {
    cursor: grab;
    overflow: hidden;
    position: relative;
    height: 155px;
    margin: 0 15px;
}

.box-slider {
    height: 100%;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 5px;
    pointer-events: none;
    position: absolute;
    top: 0;
}

.content-container {
    width: 274px;
    height: 100%;
    border-radius: 0.6em;
    background-color: #ddd;
    background-image: url(https://www.123bcc.com/home/static-game/img/cp-bg.830ac4b3.png);
    background-size: cover;
    background-position: top;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

.content-header {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding: 0.8em;
    font-size: 1.068em;
}

.content-body {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-evenly;
    padding: 0.8em;
    font-size: 1.068em;
}

.content-body span {
    margin: 0 0.285em;
    width: 2.137em;
    height: 2.137em;
    border-radius: 50%;
    background-color: #528ded;
    color: #fff;
    text-align: center;
    line-height: 2.2em;
}

.content-footer {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
    background-color: #528ded;
    padding: 0;
    font-size: 0.926em;
    line-height: 2.308em;
}

.content-footer button {
    font-family: inherit;
    display: flex;
    padding: 0 0.615em;
    font-size: 0.98em;
    font-weight: 400;
    height: 1.693em;
    border-radius: 6px;
    background-image: linear-gradient(180deg, #ffc873, #ff8e40);
    line-height: 1.6em;
    align-items: center;
    border: none;
    color: rgb(255, 255, 255);
}
</style>
  