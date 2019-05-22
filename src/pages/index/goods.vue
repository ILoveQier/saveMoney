<template>
  <div class="goods-container">
    <div class="goods-wrap">
      <article v-for="i in goodlist"
               :key="i">
        <img src="/static/images/7.jpg"
             alt="">
        <span>商品名称</span>
        <span class="good-comment">好评数:120</span>
        <div class="price">
          <span>￥88.00</span>
          <span>赠3.72</span>
        </div>
      </article>
      <div class="loading"
           :class="{isloading:isLoading}">加载中。。。</div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      goodlist: [1, 1, 1],
      isLoading: false
    }
  },
  onReachBottom() {
    this.isLoading = true
    setTimeout(() => {
      this.goodlist.push(1)
      this.isLoading = false
    }, 1000);
  }
}
</script> 
<style lang="less" scoped>
.goods-container {
  display: flex;
  .goods-wrap {
    width: 100%;
    height: fit-content;
    display: flex;
    flex-wrap: wrap;
    box-sizing: border-box;
    .loading {
      width: 100%;
      background-color: #999;
      color: #ffffff;
      height: 0;
      font-size: 0;
      font-weight: bold;
      text-align: center;
      transition: all .5s;
    }
    .isloading {
      font-size: 30rpx;
      line-height: 80rpx;
      height: 80rpx;
    }
    article {
      width: 50%;
      height: 500rpx;
      border: 2rpx solid #eee;
      box-sizing: border-box;
      display: flex;
      flex-direction: column;
      padding: 30rpx;
      font-size: 36rpx;
      img {
        width: 100%;
        height: 70%;
        margin-bottom: 20rpx;
      }
      .good-comment {
        margin: 0 0 30rpx 0;
        font-size: 24rpx;
        color: #999;
        text-align: right;
      }
      .price {
        display: flex;
        justify-content: space-between;
        align-items: center;
        span {
          color: red;
          font-size: 24rpx;
          &:nth-child(2) {
            font-size: 30rpx;
            border: 2rpx solid red;
            padding: 5rpx 20rpx;
            box-sizing: border-box;
            border-radius: 10rpx;
          }
        }
      }
    }
  }
}
</style>

