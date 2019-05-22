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
    <Classify :navFixed='scrollTop>200'></Classify>
    <Goods></Goods>
    <div class="save-btn"
         @click="goSave">
      储钱罐
    </div>
  </div>
</template>
<script>
import Classify from './classify'
import Goods from './goods'
export default {
  components: {
    Classify,
    Goods
  },
  methods: {
    goSave() {
      wx.navigateTo({
        url: '../../pages/withdraw/main',
      });
    },
  },
  data() {
    return {
      imgUrls: [],
      indicator: false,
      scrollTop: 0
    }
  },
  onPageScroll(e) {
    this.scrollTop = parseInt(e.scrollTop)
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
  height: 100%;
  .swiper-wrap {
    width: 100%;
    margin-bottom: 20rpx;
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
.save-btn {
  width: 200rpx;
  height: 200rpx;
  border-radius: 50%;
  background-color: rgb(230, 173, 220);
  color: #fff;
  text-align: center;
  line-height: 200rpx;
  position: fixed;
  bottom: 20rpx;
  right: 20rpx;
}
</style>