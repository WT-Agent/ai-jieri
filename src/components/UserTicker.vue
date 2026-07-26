<template>
  <div class="glass-card ticker-card">
    <div class="ticker-wrapper">
      <div v-for="(item, index) in tickerItems" :key="index" class="ticker-item">
        <span>{{ item.text }}</span>
        <span style="color: var(--success-color); font-weight: bold;">[生成成功]</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tickerItems = ref([
  { text: '用户 138****8892 成功生成了 [新春佳节拜年短信] 尊贵领导贺词方案' },
  { text: '用户 159****3104 成功合成了 [中秋佳节客户感谢] 高端商务贺卡文案' },
  { text: '用户 186****6617 成功解析了 [教师节感恩致敬] 深情长文致辞' },
  { text: '用户 135****9023 成功策划了 [元旦跨年倒计时] 朋友圈高赞金句' },
  { text: '用户 173****5180 成功生成了 [国庆节日促销大促] 朋友圈海报文案' },
]);
</script>

<style scoped>
.ticker-card {
  padding: 0.6rem 1rem;
  margin-bottom: 1.25rem;
  overflow: hidden;
}

.ticker-wrapper {
  display: flex;
  gap: 2rem;
  white-space: nowrap;
  animation: ticker 25s linear infinite;
}

.ticker-wrapper:hover {
  animation-play-state: paused;
}

.ticker-item {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.8rem;
  color: var(--text-secondary);
}

@keyframes ticker {
  0% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(-100%);
  }
}
</style>

