<template>
  <div class="details-container">
    <main v-if="type === 'detail'">

      <article v-for="i in list"
               :key="i">
        <div>
          <span class="title">提现失败</span>
          <span class="date">2019-04-23</span>
        </div>
        <div class="money">
          <span>余额:0.00</span>
          <span>-88.88</span>
        </div>
      </article>
      <!-- <article>
      <div>
        <span class="title">提现成功</span>
        <span class="date">2019-04-23</span>
      </div>
      <div class="money">
        <span>余额:88.88</span>
        <span>+88.88</span>
      </div>
    </article>
    <article>
      <div>
        <span class="title">消费返现</span>
        <span class="date">2019-04-23</span>
      </div>
      <div class="good-wrap">
        <span>商品名称</span>
        <span>订单号：1235498765198498484</span>
      </div>
      <div class="money">
        <span>余额:88.88</span>
        <span>+88.88</span>
      </div>
    </article> -->
      <!-- <div class="show-all">无更多显示内容</div> -->
      <div class="loading"
           :class="{isloading:isLoading}">加载中。。。</div>
    </main>
    <main v-else>
      <span class="intro">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean euismod bibendum laoreet. Proin gravida dolor sit amet lacus accumsan et viverra justo commodo. Proin sodales pulvinar tempor. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Nam fermentum, nulla luctus pharetra vulputate, felis tellus mollis orci, sed rhoncus sapien nunc eget.

        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean euismod bibendum laoreet. Proin gravida dolor sit amet lacus accumsan et viverra justo commodo. Proin sodales pulvinar tempor. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Nam fermentum, nulla luctus pharetra vulputate, felis tellus mollis orci, sed rhoncus sapien nunc eget.</span>
        <div class="show-all">无更多显示内容</div>
    </main>
  </div>
</template>
<script>
export default {
  data() {
    return {
      list: [1, 1, 1, 2, 3, 4, 5, 2],
      isLoading: false,
      type: ''
    }
  },
  onLoad() {
    this.type = this.$mp.query.type
  },
  onReachBottom() {
    this.isLoading = true
    setTimeout(() => {
      this.list.push(1)
      this.isLoading = false
    }, 3000);
  }
}
</script>
<style lang="less" scoped>
.details-container {
  padding-bottom: 50rpx;
  main {
    display: flex;
    flex-direction: column;
    box-sizing: border-box;
    align-items: center;
    .intro {
      padding: 40rpx;
      border-bottom: 2rpx solid #999;
    }
    .show-all {
      width: 100%;
      margin-top: 30rpx;
      font-size: 28rpx;
      text-align: center;
      color: #999;
    }
    article {
      width: 90%;
      border-bottom: 2rpx solid #999;
      padding: 30rpx 0;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      div {
        padding: 10rpx 30rpx;
        display: flex;
        justify-content: space-between;
        align-items: center;
        &.good-wrap {
          flex-direction: column;
          align-items: unset;
          span {
            &:nth-child(2) {
              margin-top: 10rpx;
              font-size: 30rpx;
              color: #999;
            }
          }
        }
        .title {
          font-size: 44rpx;
        }
        .date {
          font-size: 32rpx;
          color: #999;
        }
      }
      .money {
        font-size: 30rpx;
      }
    }
  }
}
.loading {
  width: 100%;
  background-color: #999;
  color: #ffffff;
  height: 0;
  font-size: 0;
  font-weight: bold;
  text-align: center;
  transition: all 0.5s;
  margin-top: 20rpx;
}
.isloading {
  font-size: 30rpx;
  line-height: 80rpx;
  height: 80rpx;
}
</style>

