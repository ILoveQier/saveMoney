<template>
  <div class="index-container">
    <swiper class="swiper-wrap"
            :indicator-dots="indicator"
            autoplay='true'
            indicator-active-color='#fff'>
      <swiper-item v-for="item in imgUrls"
                   :key="item">
        <img :src="item"
             class="slide-image" />
      </swiper-item>
    </swiper>
    <Classify></Classify>
    <Goods></Goods>
  </div>
</template>
<script>
import Classify from './classify/classify'
import Goods from './goods/goods'
export default {
  components: {
    Classify,
    Goods
  },
  data() {
    return {
      imgUrls: [],
      indicator: false
    }
  },
  onLoad() {
    this.imgUrls = ['/static/images/0.jpg', '/static/images/1.jpg', '/static/images/2.jpg', '/static/images/3.jpg', '/static/images/4.jpg', '/static/images/5.jpg']
    if (this.imgUrls.length !== 1) {
      this.indicator = true
    }
  }
}
</script>
<style lang="less">
.index-container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  overflow: hidden;
  .swiper-wrap {
    width: 100%;
    swiper-item {
      display: flex;
      justify-content: center;
      align-items: center;
      .slide-image {
        width: 700rpx;
      }
    }
  }
}
</style>
