<template>
  <!-- 使用 uni-icon 组件，并将 props 传递给它 -->
  <uni-icon
    :type="type"
    :size="size"
    :color="color"
    :custom-prefix="customPrefix"
    :src="src"
    :spin="spin"
    @click="handleClick"
  ></uni-icon>
</template>

<script lang="ts" setup>
import { defineProps, defineEmits } from 'vue';

// 定义组件的 props
const props = defineProps({
  // 图标类型，必填
  type: {
    type: String,
    required: true
  },
  // 图标大小，默认值为 24
  size: {
    type: [Number, String],
    default: 24
  },
  // 图标颜色，默认值为 #333
  color: {
    type: String,
    default: '#333'
  },
  // 自定义图标前缀
  customPrefix: {
    type: String,
    default: ''
  },
  // 自定义图标路径
  src: {
    type: String,
    default: ''
  },
  // 图标是否旋转，默认值为 false
  spin: {
    type: Boolean,
    default: false
  }
});

// 定义组件的事件
const emits = defineEmits(['click']);

// 处理图标的点击事件
const handleClick = (event:any) => {
  emits('click', event);
};
</script>

<style scoped>
/* 可根据需要添加样式 */
</style>
