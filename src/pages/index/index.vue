<template>
  <view class="homeLayout pageBg">
    <view class="banner">
      <swiper autoplay indicator-dots indicator-color="rgba(255,255,255,0.5)" indicator-active-color="#fff">
        <swiper-item v-for="item in bannerList">
          <image src="../../../common/images/banner1.jpg" mode="widthFix" />
        </swiper-item>
      </swiper>
    </view>

    <view class="notice">
      <view class="left">
        <up-icon name="volume" size="20" color="#28b389"></up-icon>
        <text class="text">公告</text>
      </view>
      <view class="center">
        <swiper vertical="true" autoplay interval="1500" duration="300" circular>
          <swiper-item v-for="(item, index) in 4" :key="index">文字内容文字内容文字内容文字内容文字内容{{ index }}</swiper-item>
        </swiper>
      </view>
      <view class="right">
        <up-icon name="arrow-right" size="16" color="#333"></up-icon>
      </view>
    </view>

    <view class="select">
      <CommonTitle>
        <template #name>每日推荐</template>
        <template #custom>
          <!-- 添加一个容器来包裹日期文本和图标 -->
          <view class="date">
            <up-icon name="calendar-fill" size="18" color="#28b389"></up-icon>
            <view class="text">
              <up-text mode="date" :text="date" format="dd日" color="#28b389"></up-text>
            </view>

          </view>
        </template>
      </CommonTitle>
      <view class="content">
        <scroll-view scroll-x>
          <view class="box" v-for="item in 8">
            <image src="../../../common/images/preview_small.webp" mode="aspectFill" />
          </view>
        </scroll-view>
      </view>
    </view>

    <view class="theme">
      <CommonTitle>
        <template #name>专题精选</template>
        <template #custom>
          <navigator url="" class="more">
            More+
          </navigator>
        </template>
      </CommonTitle>

      <view class="content">
        <ThemeItem v-for="item in 8"></ThemeItem>
        <ThemeItem :isMore="true"></ThemeItem>
      </view>
    </view>
  </view>
</template>

<script lang='ts' setup>
import { ref } from "vue"
import ThemeItem from "@/components/theme-item.vue"
// 引入组件
import CommonTitle from "../../components/common-title.vue"

const date = ref(String(Date.now()))

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
.homeLayout {
  .banner {
    width: 750rpx;
    padding: 30rpx 0;

    swiper {
      width: 750rpx;
      height: 340rpx;

      &-item {
        width: 100%;
        height: 100%;
        padding: 0 30rpx;

        image {
          width: 100%;
          height: 100%;
        }
      }
    }
  }

  .notice {
    width: 690rpx;
    height: 80rpx;
    line-height: 80rpx;
    background: #f9f9f9;
    margin: 0 auto;
    border-radius: 80rpx;
    display: flex;

    .left {
      width: 140rpx;
      display: flex;
      align-items: center;
      justify-content: center;

      .text {
        color: $brand-theme-color;
        font-weight: 600;
        font-size: 20rpx;
      }
    }

    .center {
      flex: 1;

      swiper {
        height: 100%;

        &-item {
          height: 100%;
          font-size: 30rpx;
          color: #666;
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
        }
      }
    }

    .right {
      width: 70rpx;
      line-height: 80rpx;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  }

  .select {
    padding-top: 50rpx;

    .date {
      color: $brand-theme-color;
      display: flex; // 使用 flexbox 布局
      align-items: center; // 垂直居中对齐
      gap: 8rpx; // 设置文本和图标之间的间距
    }

    .content {
      width: 720rpx;
      margin-left: 30rpx;
      margin-top: 30rpx;

      scroll-view {
        white-space: nowrap;

        .box {
          width: 200rpx;
          height: 430rpx;
          display: inline-block;
          margin-right: 15rpx;

          image {
            width: 100%;
            height: 100%;
            border-radius: 10rpx;
          }
        }

        .box:last-child {
          margin-right: 30rpx;
        }
      }
    }
  }

  .theme {
    padding: 50rpx 0;

    .more {
      font-size: 32rpx;
      color: #888;
    }

    .content{
      margin-top: 30rpx;
      padding: 0 30rpx;
      display: grid;
      gap: 15rpx;
      // bug修复：将repeat(3, 1)改为repeat(3, 1fr)
      grid-template-columns: repeat(3, 1fr);
    }
  }
}
</style>