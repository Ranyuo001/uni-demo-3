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
  <up-popup class="up-popup" :customStyle="popupCustomStyle" bgColor="#fff" mode="bottom" :show="show" @close="close"
    @open="open">
    <view class="infoPopup">
      <view class="popHeader" style="display: flex;justify-content: space-between;">
        <view></view>
        <view class="title" style="color:#676767;font-size: 26rpx;">壁纸信息</view>
        <view class="close">
          <u-icon name="close" size="20" @click="close" style="padding: 6rpx;"></u-icon>
        </view>
      </view>
      <scroll-view style="
           max-height: 60vh;

        " scroll-y>
        <view class="content">
          <view class="row" style="display: flex;padding: 16rpx 0;
          font-size: 32rpx;line-height: 1.7em;">
            <view class="label" style="
              color: #a7a7a7;
              width: 140rpx;
              text-align: right;
              font-size: 30rpx;
            ">壁纸ID:</view>
            <text class="value" selectable style="flex: 1;width: 0;">1231341411</text>
          
          </view>
          <view class="row" style="display: flex;padding: 16rpx 0;
          font-size: 32rpx;line-height: 1.7em;">
            <view class="label" style="
              color: #a7a7a7;
              width: 140rpx;
              text-align: right;
              font-size: 30rpx;
            ">分类：</view>
            <text class="value" selectable style="flex: 1;width: 0;">明星美女</text>
          
          </view>
          <view class="row" style="display: flex;padding: 16rpx 0;
          font-size: 32rpx;line-height: 1.7em;">
            <view class="label" style="
              color: #a7a7a7;
              width: 140rpx;
              text-align: right;
              font-size: 30rpx;
            ">发布者：</view>
            <text class="value" selectable style="flex: 1;width: 0;">咸虾米</text>
          
          </view>
          <view class="row" style="display: flex;padding: 16rpx 0;
          font-size: 32rpx;line-height: 1.7em;">
            <view class="label" style="
              color: #a7a7a7;
              width: 140rpx;
              text-align: right;
              font-size: 30rpx;
            ">评分：</view>
            <text class="value" selectable style="flex: 1;width: 0;">
              <up-rate :count="Ratecount" v-model="Ratevalue"></up-rate>
              <u-icon name="star-fill" size="" color="yellow"></u-icon>
            </text>
          
          </view>
          <view class="row" style="display: flex;padding: 16rpx 0;
          font-size: 32rpx;line-height: 1.7em;">
            <view class="label" style="
              color: #a7a7a7;
              width: 140rpx;
              text-align: right;
              font-size: 30rpx;
            ">摘要：</view>
            <text class="value" selectable style="flex: 1;width: 0;">
              摘要文字内容填充部分，摘要文字内容填充部分，摘要文字内容填充部分，摘要文字内容填充部分。
            </text>
          
          </view>
          <view class="row" style="display: flex;padding: 16rpx 0;
          font-size: 32rpx;line-height: 1.7em;">
            <text class="label"  style="color: #a7a7a7;width: 140rpx;text-align: right;font-size: 30rpx;">标签：</text>
							<view class='value tabs'>
								<view class="tab" v-for="item in 3">标签名</view>
							</view>
          </view>
          <!-- <view class="copyright">声明：本图片来用户投稿，非商业使用，用于免费学习交流，如侵犯了您的权益，您可以拷贝壁纸ID举报至平台，邮箱513894357@qq.com，管理将删除侵权壁纸，维护您的权益。
						
          </view> -->

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

//评分选择
const Ratecount = ref(4);  //参数设置总共有多少颗星星可选择
const Ratevalue = ref(2);  //双向绑定初始化时默认选中的星星数量

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
  // 修改 borderRadius 属性
  padding: '30rpx',
  backgroundColor: '#fff',
  borderRadius: '30rpx 30rpx 0 0',
  overflow: 'hidden',
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

  .up-popup {

    // 添加这个深度选择器来穿透组件样式
    .infoPopup {
      width: 100%;

      .popHeader {
        padding: 20rpx;

        .close {
          padding: 10rpx;
          border: 1px solid black;
        }
      }

      // scroll-view {
      //   max-height: 60vh; // 设置固定高度
      //   .content {
      //     padding: 20rpx;
      //     .row {
      //       padding: 20rpx 0;
      //     }
      //   }
    }
  }
}

.infoPopup {
  .popHeader {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
}
</style>