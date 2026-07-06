<script setup>
import { ref, onMounted } from 'vue'

const DISMISS_KEY = 'ev-cta-dismissed-until'
const visible = ref(false)

onMounted(() => {
  const until = localStorage.getItem(DISMISS_KEY)
  if (until && Date.now() < Number(until)) {
    visible.value = false
  } else {
    // 延迟显示，避免页面加载时突然出现
    setTimeout(() => { visible.value = true }, 3000)
    // 30秒后自动消失
    setTimeout(() => { visible.value = false }, 33000)
  }
})

function dismiss(days = 7) {
  visible.value = false
  const until = Date.now() + days * 24 * 60 * 60 * 1000
  localStorage.setItem(DISMISS_KEY, String(until))
}
</script>

<template>
  <Teleport to="body">
    <Transition name="cta-slide">
      <div v-if="visible" class="cta-banner" role="dialog" aria-label="学习服务推荐">
        <button class="cta-close" aria-label="关闭" @click="dismiss(7)">
          ✕
        </button>
        <div class="cta-content">
          <div class="cta-icon">🚀</div>
          <div class="cta-text">
            <div class="cta-title">🎁 免费领 AI 编程资源</div>
            <div class="cta-desc">Prompt 速查表 · 工具大全 · 模板包</div>
          </div>
          <a href="/zh-cn/resources/" class="cta-btn">免费领取</a>
        </div>
        <div class="cta-progress">
          <div class="cta-progress-bar"></div>
        </div>
      </div>
    </Transition>
  </Teleport>
</template>

<style scoped>
.cta-banner {
  position: fixed;
  bottom: 24px;
  right: 24px;
  z-index: 1000;
  max-width: 380px;
  width: calc(100vw - 48px);
  background: var(--vp-c-bg-soft);
  border: 1px solid var(--vp-c-brand-1);
  border-radius: 16px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.15), 0 0 0 1px rgba(59, 130, 246, 0.1);
  overflow: hidden;
}

.cta-content {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 16px 20px;
}

.cta-icon {
  font-size: 32px;
  flex-shrink: 0;
}

.cta-text {
  flex: 1;
  min-width: 0;
}

.cta-title {
  font-size: 15px;
  font-weight: 700;
  color: var(--vp-c-text-1);
  margin-bottom: 2px;
}

.cta-desc {
  font-size: 13px;
  color: var(--vp-c-text-2);
}

.cta-btn {
  display: inline-flex;
  align-items: center;
  padding: 8px 16px;
  background: var(--vp-c-brand-1);
  color: #fff;
  border-radius: 8px;
  font-size: 13px;
  font-weight: 600;
  text-decoration: none;
  white-space: nowrap;
  flex-shrink: 0;
  transition: background 0.2s;
}

.cta-btn:hover {
  background: var(--vp-c-brand-2);
  text-decoration: none;
  color: #fff;
}

.cta-close {
  position: absolute;
  top: 8px;
  right: 8px;
  width: 24px;
  height: 24px;
  border: none;
  background: transparent;
  color: var(--vp-c-text-3);
  font-size: 14px;
  cursor: pointer;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: color 0.2s, background 0.2s;
}

.cta-close:hover {
  color: var(--vp-c-text-1);
  background: var(--vp-c-bg-mute);
}

.cta-progress {
  height: 3px;
  background: var(--vp-c-divider);
}

.cta-progress-bar {
  height: 100%;
  background: var(--vp-c-brand-1);
  animation: cta-countdown 30s linear forwards;
}

@keyframes cta-countdown {
  from { width: 100%; }
  to { width: 0%; }
}

/* Transition */
.cta-slide-enter-active {
  transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
}

.cta-slide-leave-active {
  transition: all 0.3s ease-in;
}

.cta-slide-enter-from {
  opacity: 0;
  transform: translateY(20px) scale(0.95);
}

.cta-slide-leave-to {
  opacity: 0;
  transform: translateY(10px) scale(0.98);
}

@media (max-width: 640px) {
  .cta-banner {
    bottom: 12px;
    right: 12px;
    left: 12px;
    max-width: none;
    width: auto;
  }

  .cta-content {
    padding: 12px 16px;
    gap: 10px;
  }

  .cta-icon {
    font-size: 28px;
  }

  .cta-title {
    font-size: 14px;
  }

  .cta-desc {
    font-size: 12px;
  }
}
</style>
