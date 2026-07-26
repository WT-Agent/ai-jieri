<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">实战案例与爆款模板库 (Nomads Showcase)</h2>
        <p class="showcase-subtitle">精选高赞节日祝福与商业文案场景，点击“一键套用”快速生成专业文案</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个节日策划模板</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次应用</span>
        </div>

        <div class="card-content">
          <h3 class="item-title">{{ item.title }}</h3>
          <p class="item-prompt">“{{ item.prompt }}”</p>
        </div>

        <div class="card-action">
          <button class="apply-btn" @click="applyTemplate(item)">
            <span>一键套用</span>
            <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  prompt: string;
  festivalType?: string;
  recipientGroup?: string;
  textStyle?: string;
  usageCount: string;
}

const emit = defineEmits<{
  (e: 'apply-template', payload: {
    prompt: string;
    festivalType?: string;
    recipientGroup?: string;
    textStyle?: string;
  }): void;
}>();

const showcaseItems = computed<ShowcaseItem[]>(() => [
  {
    id: 'jieri-1',
    tag: '新春佳节',
    title: '新春佳节拜年短信与亲友贺词',
    prompt: '新春佳节拜年贺词，致亲朋好友，希望语气温馨治愈，包含对过去一年的感恩与对新年阖家幸福、身体健康的美好祝愿。',
    festivalType: '传统节日 (新春/中秋/端午/清明) 祝福',
    recipientGroup: '亲朋好友',
    textStyle: '温馨深情治愈',
    usageCount: '48.2k'
  },
  {
    id: 'jieri-2',
    tag: '中秋佳节',
    title: '中秋佳节客户高端致谢贺辞',
    prompt: '中秋佳节致战略合作伙伴与高端客户，表达对长期合作信任的诚挚感谢，预祝花好月圆、事业蒸蒸日上。',
    festivalType: '传统节日 (新春/中秋/端午/清明) 祝福',
    recipientGroup: '客户 partner',
    textStyle: '大气商务尊贵',
    usageCount: '35.6k'
  },
  {
    id: 'jieri-3',
    tag: '教师节',
    title: '教师节尊师重道感恩诗意致词',
    prompt: '教师节致恩师，表达桃李不言下自成蹊的崇高敬意，诗意典雅，提炼师恩难忘的深厚情感。',
    festivalType: '专属感恩节 (教师节/母亲节/父亲节) 致敬',
    recipientGroup: '亲朋好友',
    textStyle: '典雅古风诗意',
    usageCount: '29.4k'
  },
  {
    id: 'jieri-4',
    tag: '元旦跨年',
    title: '朋友圈迎新年跨年高赞金句',
    prompt: '元旦跨年倒计时朋友圈文案，面向年轻群体，语气幽默俏皮，告别旧岁的烦恼，拥抱新一年的幸运与美好。',
    festivalType: '西方与现代节日 (圣诞/元旦/情人节) 祝福',
    recipientGroup: '亲朋好友',
    textStyle: '幽默俏皮青春',
    usageCount: '52.1k'
  },
  {
    id: 'jieri-5',
    tag: '母亲节',
    title: '母亲节致长辈温情感悟文案',
    prompt: '母亲节致母亲，表达对岁月沉淀与无私母爱的深情致敬，配图建议温馨自然，充满治愈力量。',
    festivalType: '专属感恩节 (教师节/母亲节/父亲节) 致敬',
    recipientGroup: '长辈父母',
    textStyle: '温馨深情治愈',
    usageCount: '31.8k'
  },
  {
    id: 'jieri-6',
    tag: '国庆商业大促',
    title: '国庆黄金周品牌促销与海报文案',
    prompt: '国庆黄金周品牌大促，面向广大消费者与客户，设计极具冲击力的海报主副标题、活动促单口号与朋友圈宣发短句。',
    festivalType: '商业节点节日文案与朋友圈海报',
    recipientGroup: '客户 partner',
    textStyle: '大气商务尊贵',
    usageCount: '27.3k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt,
    festivalType: item.festivalType,
    recipientGroup: item.recipientGroup,
    textStyle: item.textStyle
  });
}
</script>

<style scoped>
.nomads-showcase-section {
  margin-top: 2rem;
  width: 100%;
}

.showcase-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1.25rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--card-border);
}

.showcase-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.showcase-subtitle {
  font-size: 0.825rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
}

.showcase-badge {
  font-size: 0.75rem;
  color: #a5b4fc;
  background: rgba(99, 102, 241, 0.12);
  border: 1px solid rgba(99, 102, 241, 0.25);
  padding: 4px 10px;
  border-radius: 20px;
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .showcase-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .showcase-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.showcase-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 1.25rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--card-border);
  border-radius: 14px;
  transition: all 0.25s ease;
}

.showcase-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.scenario-tag {
  font-size: 0.75rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 6px;
  background: rgba(168, 85, 247, 0.15);
  color: #c084fc;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

.usage-count {
  font-size: 0.75rem;
  color: var(--text-secondary);
}

.card-content {
  margin-bottom: 1rem;
  flex: 1;
}

.item-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.4rem;
}

.item-prompt {
  font-size: 0.825rem;
  color: var(--text-secondary);
  line-height: 1.45;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-style: italic;
}

.card-action {
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.04);
}

.apply-btn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 0.5rem 1rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  border-radius: 8px;
  color: #a5b4fc;
  font-size: 0.825rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.showcase-card:hover .apply-btn {
  background: var(--primary-gradient);
  border-color: transparent;
  color: white;
}

.arrow-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.2s ease;
}

.apply-btn:hover .arrow-icon {
  transform: translateX(3px);
}
</style>

