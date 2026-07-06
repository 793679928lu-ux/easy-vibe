<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({
  tool: { type: String, required: true },
  action: { type: String, default: '注册使用' },
  url: { type: String, required: true },
  benefit: { type: String, default: '' },
  code: { type: String, default: '' }
})

const isVisible = ref(false)

onMounted(() => {
  // Delay slight reveal for visual impact when user scrolls to it
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) {
      setTimeout(() => { isVisible.value = true }, 200)
      observer.disconnect()
    }
  }, { threshold: 0.3 })

  // Find the element this component is mounted on
  const el = document.querySelector('[data-inline-referral]')
  if (el) observer.observe(el)
})
</script>

<template>
  <div class="inline-referral" :class="{ visible: isVisible }" data-inline-referral>
    <div class="ir-header">
      <span class="ir-icon">💡</span>
      <span class="ir-title">试试 <strong>{{ tool }}</strong></span>
    </div>
    <p class="ir-desc">
      我们在课程中深度使用的工具。<span v-if="benefit">{{ benefit }}</span>
      <span v-if="code" class="ir-code">推荐码：<code>{{ code }}</code></span>
    </p>
    <a :href="url" target="_blank" rel="noopener sponsored" class="ir-btn">
      {{ action }} →
    </a>
  </div>
</template>

<style scoped>
.inline-referral {
  margin: 24px 0;
  padding: 20px 24px;
  background: linear-gradient(135deg, var(--vp-c-bg-soft), var(--vp-c-brand-soft));
  border: 1px solid var(--vp-c-brand-1);
  border-radius: 12px;
  opacity: 0;
  transform: translateY(8px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.inline-referral.visible {
  opacity: 1;
  transform: translateY(0);
}

.ir-header {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-bottom: 8px;
}

.ir-icon {
  font-size: 20px;
}

.ir-title {
  font-size: 16px;
  font-weight: 600;
  color: var(--vp-c-text-1);
}

.ir-title strong {
  color: var(--vp-c-brand-1);
}

.ir-desc {
  font-size: 14px;
  color: var(--vp-c-text-2);
  margin: 0 0 12px;
  line-height: 1.6;
}

.ir-code {
  display: inline-block;
  margin-left: 4px;
  font-size: 13px;
}

.ir-code code {
  background: var(--vp-c-bg);
  padding: 2px 8px;
  border-radius: 4px;
  font-size: 13px;
  color: var(--vp-c-brand-1);
  font-weight: 600;
}

.ir-btn {
  display: inline-flex;
  align-items: center;
  padding: 8px 20px;
  background: var(--vp-c-brand-1);
  color: #fff;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  text-decoration: none;
  transition: background 0.2s, transform 0.2s;
}

.ir-btn:hover {
  background: var(--vp-c-brand-2);
  text-decoration: none;
  color: #fff;
  transform: translateX(2px);
}
</style>
