<template>
  <view class="userLayout pageBg">
    <view class="userInfo">
      <view class="avatar">
        <image src="../../static/images/xxmLogo.png"></image>
      </view>
      <view class="ip">127.0.0.1</view>
      <view class="address">
        来自于:山东
      </view>
    </view>


    <view class="section">
      <view class="list">
        <navigator url="/pages/index/classlist">
          <userItem :iconName="iconList[0].iconName">
            <template #name>我的下载</template>
            <template #userItemNum>33</template>
          </userItem>
        </navigator>
        
        <navigator url="/pages/index/classlist">
          <userItem :iconName="iconList[1].iconName">
            <template #name>我的评分</template>
            <template #userItemNum>33</template>
          </userItem>
        </navigator>
        
        <userItem :iconName="iconList[2].iconName">
          <template #name>联系客服</template>
          <template #userItemNum>

          </template>
          <template #button>
            <!-- #ifdef MP-WEIXIN -->
            <button class="listButton" open-type="contact">联系客服</button>
            <!-- #endif -->
            <!-- #ifdef H5 -->
            <button class="listButton" @click="clickContact">拨打电话</button>
            <!-- #endif -->
          </template>
        </userItem>
      </view>
    </view>
    <view class="section">
      <view class="list">
        <userItem :iconName="iconList[3].iconName">
          <template #name>订阅更新</template>
        </userItem>
      </view>
      <view class="list">
        <userItem :iconName="iconList[4].iconName">
          <template #name>常见问题</template>
        </userItem>
      </view>
    </view>
  </view>
</template>

<script lang='ts' setup>
import { ref } from "vue";
import userItem from "@/components/userItem.vue";

// 封装成数组对象,图标数组
const iconList = ref([
  { iconName: 'download' },
  { iconName: 'star-fill' },
  { iconName: 'chat-fill' },
  { iconName: 'bell-fill' },
  { iconName: 'more-circle-fill' }
]);
//拨打电话
const clickContact = () => {
  uni.makePhoneCall({
    phoneNumber: '13888888888'
  });
};
</script>

<style lang="scss" scoped>
.userLayout {
  .userInfo {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    padding: 50rpx 0;

    .avatar {
      width: 160rpx;
      height: 160rpx;
      border-radius: 50%;
      overflow: hidden;

      image {
        width: 100%;
        height: 100%;
      }
    }

    .ip {
      font-size: 44rpx;
      color: #333;
      padding: 20rpx 0 5rpx;
    }

    .address {
      font-size: 28rpx;
      color: #aaa;
    }
  }

  .section {
    width: 690rpx;
    margin: 50rpx auto;
    border: 1px solid #eee;
    border-radius: 10rpx;
    box-shadow: 0 0 30rpx rgba(0, 0, 0, 0.05);

    .listButton {
      position: absolute;
      left: 0;
      left: 0;
      height: 100rpx;
      width: 100%;
      opacity: 0;
    }
  }
}
</style>