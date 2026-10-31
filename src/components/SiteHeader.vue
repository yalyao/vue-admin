<template>
  <header class="site-header" :class="{ scrolled: isScrolled }">
    <div class="container header-inner">
      <router-link to="/" class="logo">
        <span class="logo-icon">🚀</span>
        <span class="logo-text">科技有限公司</span>
      </router-link>
      <nav class="nav-menu" :class="{ active: mobileMenuOpen }">
        <router-link
          v-for="item in navItems"
          :key="item.path"
          :to="item.path"
          class="nav-item"
          active-class="nav-item-active"
          @click="mobileMenuOpen = false"
        >
          {{ item.name }}
        </router-link>
      </nav>
      <button class="mobile-toggle" @click="mobileMenuOpen = !mobileMenuOpen">
        <span :class="{ open: mobileMenuOpen }"></span>
        <span :class="{ open: mobileMenuOpen }"></span>
        <span :class="{ open: mobileMenuOpen }"></span>
      </button>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const mobileMenuOpen = ref(false)

const navItems = [
  { path: '/', name: '首页' },
  { path: '/about', name: '关于我们' },
  { path: '/services', name: '产品服务' },
  { path: '/news', name: '新闻资讯' },
  { path: '/contact', name: '联系我们' }
]

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.site-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background-color: transparent;
  transition: all 0.3s;
}

.site-header.scrolled {
  background-color: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.08);
}

.header-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 70px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 20px;
  font-weight: 700;
  color: #303133;
}

.logo-icon {
  font-size: 28px;
}

.nav-menu {
  display: flex;
  gap: 32px;
}

.nav-item {
  font-size: 15px;
  color: #606266;
  font-weight: 500;
  transition: color 0.3s;
  position: relative;
}

.nav-item:hover {
  color: #409eff;
}

.nav-item-active {
  color: #409eff;
}

.nav-item-active::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 0;
  right: 0;
  height: 2px;
  background-color: #409eff;
  border-radius: 1px;
}

.mobile-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 5px;
}

.mobile-toggle span {
  width: 24px;
  height: 2px;
  background-color: #303133;
  border-radius: 2px;
  transition: all 0.3s;
}

@media (max-width: 768px) {
  .mobile-toggle {
    display: flex;
  }

  .nav-menu {
    position: absolute;
    top: 70px;
    left: 0;
    right: 0;
    background-color: #fff;
    flex-direction: column;
    padding: 20px;
    gap: 16px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
    transform: translateY(-20px);
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s;
  }

  .nav-menu.active {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
  }

  .nav-item-active::after {
    bottom: -4px;
  }

  .logo-text {
    font-size: 16px;
  }
}
</style>