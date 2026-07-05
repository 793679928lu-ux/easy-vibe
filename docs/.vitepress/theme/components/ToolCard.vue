<script setup>
defineProps({
  name: { type: String, required: true },
  tag: { type: String, default: '' },
  description: { type: String, required: true },
  url: { type: String, required: true },
  pricing: { type: String, default: '' },
  pros: { type: String, default: '' },
  affiliate: { type: String, default: '' },
  affiliateLink: { type: String, default: '' },
  affiliateLabel: { type: String, default: '' }
})

const tagColors = {
  '首推': '#f59e0b',
  'Top Pick': '#f59e0b',
  '最强': '#ef4444',
  'Most Powerful': '#ef4444',
  '免费': '#22c55e',
  'Free': '#22c55e',
  '必备': '#3b82f6',
  'Essential': '#3b82f6',
  '专业': '#8b5cf6',
  'Professional': '#8b5cf6',
  'AI': '#ec4899',
  '首选': '#06b6d4',
  'Go-To': '#06b6d4',
  '开源': '#84cc16',
  'Open Source': '#84cc16',
  '简单': '#14b8a6',
  'Simple': '#14b8a6',
  '全面': '#f97316',
  'Comprehensive': '#f97316'
}

function getTagColor(tag) {
  return tagColors[tag] || '#64748b'
}
</script>

<template>
  <div class="tool-card">
    <div class="tool-card-header">
      <h3 class="tool-name">{{ name }}</h3>
      <span v-if="tag" class="tool-tag" :style="{ background: getTagColor(tag) }">
        {{ tag }}
      </span>
    </div>
    <p class="tool-desc">{{ description }}</p>
    <div v-if="pricing" class="tool-pricing">
      <span class="label">💰 价格：</span>{{ pricing }}
    </div>
    <div v-if="pros" class="tool-pros">
      <span class="label">✅ 亮点：</span>{{ pros }}
    </div>
    <div class="tool-actions">
      <a :href="url" target="_blank" rel="noopener sponsored" class="tool-btn">
        前往官网 →
      </a>
      <a
        v-if="affiliateLink"
        :href="affiliateLink"
        target="_blank"
        rel="noopener"
        class="tool-affiliate-link"
      >
        {{ affiliateLabel || '💰 申请联盟计划' }}
      </a>
      <span v-else-if="affiliate" class="tool-affiliate-badge" title="通过此链接注册我们可能获得返佣">
        🎁 专属优惠
      </span>
    </div>
  </div>
</template>

<style scoped>
.tool-card {
  background: var(--vp-c-bg-soft);
  border: 1px solid var(--vp-c-divider);
  border-radius: 12px;
  padding: 20px;
  transition: border-color 0.2s, box-shadow 0.2s;
  display: flex;
  flex-direction: column;
}

.tool-card:hover {
  border-color: var(--vp-c-brand-1);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);
}

.tool-card-header {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}

.tool-name {
  font-size: 18px;
  font-weight: 700;
  margin: 0;
  color: var(--vp-c-text-1);
}

.tool-tag {
  font-size: 11px;
  font-weight: 600;
  color: #fff;
  padding: 2px 8px;
  border-radius: 4px;
  white-space: nowrap;
}

.tool-desc {
  font-size: 14px;
  color: var(--vp-c-text-2);
  margin: 0 0 12px;
  line-height: 1.6;
  flex: 1;
}

.tool-pricing,
.tool-pros {
  font-size: 13px;
  color: var(--vp-c-text-2);
  margin-bottom: 6px;
  line-height: 1.5;
}

.tool-pricing .label,
.tool-pros .label {
  font-weight: 600;
  color: var(--vp-c-text-1);
}

.tool-actions {
  margin-top: 14px;
  display: flex;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
}

.tool-btn {
  display: inline-flex;
  align-items: center;
  padding: 8px 18px;
  background: var(--vp-c-brand-1);
  color: #fff;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  text-decoration: none;
  transition: background 0.2s;
}

.tool-btn:hover {
  background: var(--vp-c-brand-2);
  text-decoration: none;
  color: #fff;
}

.tool-affiliate-badge {
  font-size: 12px;
  color: var(--vp-c-brand-1);
  font-weight: 500;
}

.tool-affiliate-link {
  font-size: 11px;
  color: var(--vp-c-brand-2);
  text-decoration: none;
  padding: 6px 12px;
  border: 1px dashed var(--vp-c-brand-1);
  border-radius: 6px;
  transition: all 0.2s;
  white-space: nowrap;
}

.tool-affiliate-link:hover {
  background: var(--vp-c-brand-soft);
  text-decoration: none;
}
</style>
