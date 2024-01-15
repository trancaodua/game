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
            // e.preventDefault();

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
  