<template>
  <div class="carousel">
    <div class="image-container" ref="imgs" :style="{ transform: transform }">
      <img v-for="image in data" :key="image.key" :src="image.src" :alt="image.key" />
    </div>
    <div class="carousel-swiper">
      <a class="icon-dot" :class="{ active: idx == index + 1 }" v-for="(image, index) in data" :key="image.key"
        href="#"><i></i></a>
    </div>
    <div class="online-user">
      <i class="online_user_icon"></i>
      <span>396463</span>
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
        src: "https://upload.vn5959.com/p/20240110/lion/28/10367280/jpg/1704876092565.jpg"
      },
      {
        key: 1,
        src: "https://upload.vn5959.com/p/20240110/lion/28/10367280/jpg/1704876064301.jpg"
      },
      {
        key: 2,
        src: "https://upload.vn5959.com/p/20240110/lion/28/10367280/jpg/1704876078477.jpg"
      },
      {
        key: 3,
        src: "https://upload.vn5959.com/p/20240110/lion/28/10367280/jpg/1704876078477.jpg"
      },
      {
        key: 4,
        src: "https://upload.vn5959.com/p/20240110/lion/28/10367280/jpg/1704876064301.jpg"
      },
      {
        key: 5,
        src: "https://upload.vn5959.com/p/20240110/lion/28/10367280/jpg/1704876092565.jpg"
      },
      {
        key: 6,
        src: "https://upload.vn5959.com/p/20240110/lion/28/10367280/jpg/1704876092565.jpg"
      },
      {
        key: 7,
        src: "https://upload.vn5959.com/p/20240110/lion/28/10367280/jpg/1704876092565.jpg"
      }
    ]
    const imgs = ref(null);
    const idx = ref(0)
    const transform = "translateX(0)";
    let interval = ref(null);

    // expose to template and other options API hooks
    return {
      imgs,
      idx,
      data,
      transform,
      interval
    }
  },

  mounted() {
    this.interval = setInterval(this.run, 2000);
  },
  unmounted() {
    alert("The component is removed (unmounted)!");
    clearInterval(this.interval);
  },
  methods: {
    run() {
      this.changeImage();
      this.idx++;
    },
    changeImage() {
      if (this.idx > this.data.length - 1) {
        this.idx = 0;
      }
      else if (this.idx < 0) {
        this.idx = this.data.length - 1;
      }
      this.transform = `translateX(${-this.idx * this.imgs.offsetWidth}px)`;
      console.log(this.idx);
    }
  }
}
</script>
  
<style scoped>
.carousel {
  width: 100%;
  height: 145px;
  overflow: hidden;
  position: relative;
}

.image-container {
  display: flex;
  transform: translateX(0);
  transition: transform 0.5s ease-in-out;
  height: 100%;
}

.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.carousel-swiper {
  position: absolute;
  bottom: 5%;
  left: 50%;
  transform: translateX(-50%);
}

.icon-dot {
  display: inline-block;
  vertical-align: middle;
  width: 6px;
  height: 6px;
  border-radius: 3px;
  background-color: #d0cdd1;
  margin-left: 6px;
}

.icon-dot.active {
  background-color: #04be02;
}

.online-user {
  position: absolute;
  top: 0.6em;
  right: 0.3em;
  z-index: 101;
  display: flex;
  align-items: center;
  padding: 0 0.8em;
  height: 1.64em;
  border-radius: 1em;
  background-color: rgba(0, 0, 0, 0.4);
  color: #fff;
  font-size: 0.8em;
  line-height: 1.83em;
}

.online_user_icon {
  margin-top: -0.1em;
  margin-right: 0.4em;
  width: 0.9em;
  height: 1.1em;
  background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAUCAYAAACEYr13AAAAAXNSR0IArs4c6QAAAERlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAA6ABAAMAAAABAAEAAKACAAQAAAABAAAAEKADAAQAAAABAAAAFAAAAADB1dcyAAABL0lEQVQ4EZWRvU5CQRCFd0m0IRg7ow9ArAmPYEJrRUV4DB/CTh7ARFopCAkdjRZQ8QDWKp3Gn5iAJl6/kd11bu5eWTY5mTNnzhl2L8ZETpZlLTACj2DheCtiLUqYL0DZ6RUTSiHVKUsqvaMieYrpXhnL6EM+5Trch2WJiH7kl1Q8oR4ovokGr/VOfmUX/g6k/ne+GNastSsxhRsgfNKPRdxwxj5c8Lnv8BR5s5eexVMIagFDHUx9QtWZzLRXePgGeoBRntYATafPqXOu/u36UHILCJ4w6YJjUA2uNfmg3IErFk1yM4I1cAlSj3j3whKa69Sk8g1+FyC0lbgtbRsSN9umlP/W0rxylb/3hIclkTf5u5ZJ1rhpKQv68VmS2pcn7GA9A6dgPylmzAu+ITj/AcdoA2aIRhSnAAAAAElFTkSuQmCC);
  background-size: 0.9em 1.1em;
}
</style>
  