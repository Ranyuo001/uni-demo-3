<template>
  <view class="theme-item">
    <navigator url="" class="box" v-if="!isMore">
      <image class="pic" src="../../common/images/classify1.jpg" mode="aspectFill"></image>
      <view class="mask">美女明星</view>
      <view class="tab">3天前更新</view>
    </navigator>

    <navigator url="" class="box more" v-if="isMore">
      <image class="pic" src="../../common/images/more.jpg" mode="aspectFill"></image>
      <view class="mask">
        <up-icon name="more-dot-fill" size="34" color="#fff"></up-icon>
        <text class="text">更多</text>
      </view>
    </navigator>
  </view>
</template>

<script lang="ts" setup>
  defineProps({
    isMore:{
      type:Boolean,
      default:false
    }
  })
</script>

<style lang="scss" scoped>
.theme-item{
  .box{
    height: 340rpx;
    border-radius: 10rpx;
    overflow: hidden;
    position: relative;
    .pic{
      width: 100%;
      height: 100%;
    }
    .mask{
      width: 100%;
      height: 70rpx;
      position: absolute;
      bottom: 0;
      left: 0;
      background: rgba(0,0,0,0.2);
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      backdrop-filter: blur(20rpx);
      font-weight: 600;
      font-size: 30rpx;
    }
    .tab{
      position: absolute;
      left: 0;
      top: 0;
      background: rgba(250,129,90,0.7);
      backdrop-filter: blur(20rpx);
      color: #fff;
      font-size: 22rpx;
      padding: 6rpx 14rpx;
      border-radius: 0 0 10rpx 0
    }
  }
  .box.more{
    .mask{
      height: 100%;
      height: 100%;
      flex-direction: column;
    }
    .text{
      font-size: 28rpx;
    }
  }
}
</style>