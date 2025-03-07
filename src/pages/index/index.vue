<template>
  <view class="homeLayout">
    <view class="banner">
      <swiper autoplay indicator-dots indicator-color="rgba(255,255,255,0.5)" indicator-active-color="#fff">
        <swiper-item v-for="item in bannerList">
          <image
            src="../../../common/images/banner1.jpg"
            mode="widthFix"
          />
        </swiper-item>
      </swiper>
    </view>

    <view class="notice">
      <view class="left">
        <up-icon name="volume"></up-icon>
        <up-icon name="photo" color="#2979ff" size="28"></up-icon>
      </view>
      <view class="center"></view>
      <view class="right"></view>
    </view>
  </view>
</template>

<script lang='ts' setup>
import {ref} from "vue"

// 轮播图数据
const bannerList = ref<any[]>([
  {
    id: "qwqeasdsa01",
    img: '../../../common/images/banner1.jpg' 
  },
  {
    id: "qwqeasdsa02",
    img: '../../../common/images/banner2.jpg' 
  },
  {
    id: "qwqeasdsa03",
    img: '../../../common/images/banner3.jpg' 
  },
])
</script>

<style lang="scss" scoped>
.homeLayout{
  .banner{
    width: 750rpx;
    padding: 30rpx 0;
    swiper{
      width: 750rpx;
      height: 340rpx;
      &-item{
        width: 100%;
        height: 100%;
        padding: 0 30rpx;
        image{
          width: 100%;
          height: 100%;
        }
      }
    }
  }
}
</style>