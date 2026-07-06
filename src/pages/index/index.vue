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

const title = ref('加载中...')

uni.request({
  url: 'https://lyt.juntaitec.cn/test',
  method: 'GET',
  timeout: 10000,   // 10 秒超时（可按需调整）
  success: (res) => {
    console.log('请求成功', res.data)
    title.value = res.data as string
  },
  fail: (err) => {
    console.error('请求失败', err)
    title.value = '网络请求失败'
    uni.showToast({ title: '请求超时，请检查网络', icon: 'none' })
  }
})
</script>