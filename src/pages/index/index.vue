<template>
  <view class="container">
    <view class="header">首页</view>
    <view class="content">
      <text>欢迎来到移动商城首页11！{{title}}</text>
    </view>
  </view>
</template>

<script setup lang="ts">
import {ref} from 'vue'
const title=ref('')
// 逻辑层代码
uni.request({
  url: 'https://lyt.juntaitec.cn/test',
  data: {
    text: 'uni.request'
  },
  // header: {
  //   'custom-header': 'hello' //自定义请求头信息
  // },
  success: (res) => {
    console.log("坎坎坷坷",res.data);
    title.value = res.data;
  }
});
</script>

<style scoped>
.container { padding: 20px; }
.header { font-size: 24px; font-weight: bold; margin-bottom: 20px; color: #333; }
.content { color: #666; font-size: 16px; }
</style>