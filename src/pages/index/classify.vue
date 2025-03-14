<template>
  <view class="classLayout pageBg">
    <view class="classify">
      <ThemeItem v-for="item in 15"></ThemeItem>
    </view>
  </view>
</template>

<script lang='ts' setup>
import ThemeItem from "@/components/theme-item.vue"
</script>

<style lang="scss" scoped>
.classify{
  padding: 30rpx;
  display: grid;
  grid-template-columns: repeat(3,1fr);
  gap: 15rpx;

}
</style>