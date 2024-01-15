<template>
  <header v-if="!close">
    <div  class="sub-left-header">
      <div class="close-container" @click="handleClose">
        <div class="close-icon"></div>
      </div>
      <div class="phone-icon"></div>
      <div class="header-text">Nhập và tải xuống ứng dụng</div>
    </div>
    <div class="download-icon"></div>
  </header>
</template>


<script>
import { ref } from 'vue'

export default {
  setup() {
     let close = ref(false);
    

    // expose to template and other options API hooks
    return {
      close 
    }
  },
  methods: {
    handleClose() {
      this.close = true;
    }
  }
}
</script>
  
<style scoped>
/* Header */
header {
  height: 52px;
  display: flex;
  align-items: center;
  flex-direction: row;
  justify-content: space-between;
  background-color: rgb(22, 107, 226);
  font-size: 1.25rem;
  flex-shrink: 0;
  position: sticky;
  top: 0;
  z-index: 100;
}

.sub-left-header {
  display: flex;
  flex-direction: row;
  align-items: center;
}

.close-container {
  width: 60px;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.close-icon {
  width: 12px;
  height: 12px;
  background-image: url(https://www.123bcc.com/home/static-game/img/close.c0fb03a8.svg);
  background-repeat: no-repeat;
  background-size: contain;
  background-origin: center;
}

.phone-icon {
  width: 16px;
  height: 23px;
  background-image: url(https://www.123bcc.com/home/static-game/img/device.4836baaa.svg);
  background-repeat: no-repeat;
  background-size: contain;
  background-origin: center;
}

.header-text {
  padding-left: 5px;
}

.download-icon {
  width: 60px;
  height: 100%;
  background-image: url(https://www.123bcc.com/home/static-game/img/downloads.f8df7136.svg);
  background-position: 50%;
  background-repeat: no-repeat;
  background-size: 20px auto;
  background-origin: center;
}

/* End Header */
</style>
  