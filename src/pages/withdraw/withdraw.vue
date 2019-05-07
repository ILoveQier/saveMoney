<template>
  <div class="draw-container">
    <div class="surplus">
      <span>储钱罐余额</span>
      <span>{{surplus}}</span>
    </div>
    <div class="cash-out"
         :class="{beGray:surplus <= 0}"
         @click="goWithDraw">提现</div>
    <div class="warning">
      注：提现将以微信红包形式发送到当前提现微信号，请先关注公众号“奇趣箱玩具故事”再提现。
    </div>
    <div class="details"
         @click="goDetails('detail')">
      <span>账单明细</span>
      <span class="arrow"></span>
    </div>
    <div class="details" @click="goDetails('')">
      <span>关于储钱罐</span>
      <span class="arrow"></span>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      surplus: 0
    }
  },
  methods: {
    goDetails(type) {
      wx.navigateTo({
        url: './details/main?type='+type,
      });
    },
    goWithDraw() {
      if (this.surplus <= 0) {
        return
      }
      wx.showModal({
        title: '提现成功！^_^',
        content: '请到公众号"奇趣箱玩具故事"查收红包',
        showCancel: false,
        confirmText: '确定',
        confirmColor: '#FF6699',
        success: (result) => {
        },
      });
    }
  },
  onLoad() {
    this.surplus = 1
  }
}
</script> 
<style lang="less" scoped>
.draw-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 50rpx;
  .surplus {
    width: 100%;
    height: 300rpx;
    background-color: #eee;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    padding: 50rpx 0;
    box-sizing: border-box;
    span:nth-child(2) {
      font-size: 54rpx;
    }
  }
  .cash-out {
    margin: 40rpx 0;
    width: 100%;
    height: 80rpx;
    text-align: center;
    line-height: 80rpx;
    color: #ffffff;
    font-size: 32rpx;
    background-color: #ff6699;
    &.beGray {
      background-color: #999;
    }
  }
  .warning {
    width: 88%;
    color: red;
    font-size: 26rpx;
    text-indent: 5%;
    margin-bottom: 50rpx;
  }
  .details {
    width: 100%;
    height: 90rpx;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 2rpx solid #ccc;
    font-size: 28rpx;
    .arrow {
      width: 0;
      height: 0;
      border: 20rpx solid;
      border-color: transparent transparent transparent #117bff;
      margin-right: -10rpx;
      position: relative;
    }
    .arrow::after {
      content: "";
      position: absolute;
      transform: translate(-50%, -50%);
      left: -5rpx;
      border: 30rpx solid;
      border-color: transparent transparent transparent #fff;
    }
  }
}
</style>

