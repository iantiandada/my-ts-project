<template>
  <view class="container">
    <view class="header">首页</view>
    <view class="content">
      <text>欢迎来到移动商城首页121！{{ title }}</text>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const title = ref('')

uni.request({
  url: 'https://lyt.juntaitec.cn/test',
  method: 'GET',
  timeout: 10000,
  success: (res) => {
    title.value = res.data as string
  },
  fail: (err) => {
    console.error('请求失败', err)
    // 显示完整错误对象
    uni.showModal({
      title: '请求失败',
      content: JSON.stringify(err),
      showCancel: false
    })
    title.value = '网络请求失败'
  }
})
</script>