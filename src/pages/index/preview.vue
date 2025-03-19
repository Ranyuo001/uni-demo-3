<template>
  <view class="preview">
    <swiper circular>
      <swiper-item v-for="item in 5">
        <!-- 图片组件，显示固定路径的图片，mode 为 scaleToFill 表示缩放填充 -->
        <image @click="maskChange" src="../../../common/images/preview1.jpg" mode="scaleToFill" />
      </swiper-item>
    </swiper>

    <!-- 遮罩层视图 -->
    <view class="mask" v-if="maskState">
      <view class="goBack">←</view>
      <view class="count">3 / 9</view>
      <view class="time">
        <up-text size="140rpx" mode="date" :text="date" format="hh:mm" color="#fff"></up-text>
      </view>
      <view class="date">
        <up-text size="34rpx" class="date" mode="date" :text="date" format="mm月dd日" color="#fff"></up-text>
      </view>
      <template>
      </template>
      <view class="footer">
        <view class="box" @click="show = true">
          <u-icon name="info" size="28"></u-icon>
          <view class="text">信息</view>
        </view>
        <view class="box">
          <u-icon name="star-fill" size="28"></u-icon>
          <view class="text">分数</view>
        </view>
        <view class="box">
          <u-icon name="download" size="28"></u-icon>
          <view class="text">下载</view>
        </view>
      </view>
    </view>
  </view>
  <up-popup :customStyle="popupCustomStyle" bgColor="#fff" mode="center" :show="show" @close="close" @open="open">
    <view class="infoPopup">
      <view class="popHeader">
        <view></view>
        <view class="title">壁纸信息</view>
        <view class="close">
          <u-icon name="close" size="20" @click="close"></u-icon>
        </view>
      </view>
      <scroll-view scroll-y>
        <view class="content">
          <view class="row" v-for="item in 10">{{ item }}</view>
        </view>
      </scroll-view>
    </view>
  </up-popup>
</template>

<script lang='ts' setup>
import { ref } from 'vue'
const date = ref(String(Date.now()))
const maskState = ref(true);
const show = ref(true);

// 定义方法  
function open() {
  // 打开逻辑，比如设置 show 为 true  
  show.value = true;
  // console.log('open');  
}

function close() {
  // 关闭逻辑，设置 show 为 false  
  show.value = false;
  // console.log('close');  
}

//点击info弹窗
// const clickInfo = () =>{
//   infoPopup.value.open
// }

//遮罩
const maskChange = () => {
  maskState.value = !maskState.value;
}

//自定义样式
const popupCustomStyle = ref({
  width: '80%',
  height: '80%',
  // 修改 borderRadius 属性
  borderRadius: '30rpx 30rpx 0 0',
  backgroundColor: '#fff',
  boxShadow: '0 4rpx 8rpx rgba(0, 0, 0, 0.1)',
  // 修正 backdropFilter 属性的引号闭合问题
  backdropFilter: 'blur(20rpx)'
})
</script>

<style lang="scss" scoped>
.view {
  background-color: none;
}

.preview {
  width: 100%;
  height: 100vh;
  position: relative;

  swiper {
    width: 100%;
    height: 100%;

    image {
      width: 100%;
      height: 100%;
    }
  }

  .mask {
    &>view {
      // 定位在遮罩层内水平居中
      position: absolute;
      left: 0;
      right: 0;
      margin: auto;
      color: #fff;
      // 宽度根据内容自适应
      width: fit-content;
    }

    .goBack {
      // 这里可以添加返回按钮的样式
    }

    .count {
      top: 10vh;
      background: rgba(0, 0, 0, 0.3);
      font-size: 28rpx;
      border-radius: 40rpx;
      padding: 8rpx 28rpx;
      // 毛玻璃效果
      backdrop-filter: blur(20rpx);
    }

    ::v-deep .time {
      font-size: 140rpx;
      top: calc(10vh + 80rpx);
      font-weight: 100;
      line-height: 1em;
      text-shadow: 0 4rpx rgba(0, 0, 0, 0.3);
    }

    ::v-deep .date {
      font-size: 34rpx;
      top: calc(10vh + 210rpx);
      text-shadow: 0 2rpx rgba(0, 0, 0, 0.3);
    }

    .footer {
      background: rgba(255, 255, 255, 0.8);
      bottom: 10vh;
      width: 65vw;
      height: 120rpx;
      border-radius: 120rpx;
      color: #000;
      display: flex;
      justify-content: space-around;
      align-items: center;
      box-shadow: 0 4rpx 8rpx rgba(0, 0, 0, 0.1);
      backdrop-filter: blur(20rpx);

      .box {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 2rpx 12rpx;

        .text {
          font-size: 26rpx;
          color: $text-font-color-2;
        }
      }
    }
  }

  .up-popuo {
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.3);
    border-radius: 30rpx 30rpx 0 0;

    .infoPopup {

    }
  }


}
</style>