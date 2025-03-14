<template>
  <div class="userItem">
    <view class="row">
      <view class="left">
        <up-icon :name="iconName" size="30" color="#28b389"></up-icon>
        <view class="text">
          <slot name="name"></slot>
        </view>
      </view>
      <view class="right">
        <view class="text">
          <slot name="userItemNum"></slot>
          <slot></slot>
        </view>
        <up-icon name="arrow-right" size="15" color="#aaa"></up-icon>
        <slot name="button"></slot>
      </view>
    </view>
  </div>
</template>

<script lang="ts" setup>
  import { defineProps } from 'vue';

// 定义接收的 props
const props = defineProps({
  iconName: {
    type: String,
    default: 'download'
  }
});
console.log(props);

</script>

<style lang="scss" scoped>
  .userItem {
    .row {
      background: #fff;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0 30rpx;
      height: 100rpx;
      border-bottom: 1px solid #eee;
      // 给除了最后一个 .row 元素添加底部边框
      &:not(:last-child) {
        border-bottom: 1px solid #eee;
      }
      position: relative;
      .left{
        display: flex;
        align-items: center;
        .text{
          padding-left: 20rpx;
          color: #666;
        }
      }
      .right{
        display: flex;
        align-items: center;
        .text{
          font-size: 28rpx;
          color: #aaa;

        }
      }

    }
  }
</style>