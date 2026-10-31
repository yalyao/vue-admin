<template>
  <div class="layout-container">
    <el-container class="layout-main">
      <el-aside width="200px" class="layout-sidebar">
        <div class="sidebar-logo">
          <h2>Vue Admin</h2>
        </div>
        <el-menu
          :default-active="activeMenu"
          class="sidebar-menu"
          router
        >
          <el-menu-item index="/dashboard">
            <el-icon><i-ep-home /></el-icon>
            <span>首页</span>
          </el-menu-item>
          <el-menu-item index="/user">
            <el-icon><i-ep-user /></el-icon>
            <span>用户管理</span>
          </el-menu-item>
          <el-menu-item index="/role">
            <el-icon><i-ep-position /></el-icon>
            <span>角色管理</span>
          </el-menu-item>
          <el-menu-item index="/menu">
            <el-icon><i-ep-menu /></el-icon>
            <span>菜单管理</span>
          </el-menu-item>
        </el-menu>
      </el-aside>
      <el-container>
        <el-header class="layout-header">
          <div class="header-left">
            <el-button type="text" @click="toggleSidebar">
              <el-icon><i-ep-menu /></el-icon>
            </el-button>
          </div>
          <div class="header-right">
            <el-dropdown>
              <span class="user-info">
                <el-avatar :size="32" src="https://cube.elemecdn.com/3/7c/3ea6beec64369c2642b92c6726f1epng.png" />
                <span>管理员</span>
                <el-icon class="el-icon--right"><i-ep-arrow-down /></el-icon>
              </span>
              <template #dropdown>
                <el-dropdown-menu>
                  <el-dropdown-item>个人中心</el-dropdown-item>
                  <el-dropdown-item @click="logout">退出登录</el-dropdown-item>
                </el-dropdown-menu>
              </template>
            </el-dropdown>
          </div>
        </el-header>
        <el-main class="layout-content">
          <router-view />
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue'
import { useRouter } from 'vue-router'
import { ElMessage } from 'element-plus'

const router = useRouter()
const sidebarCollapse = ref(false)

const activeMenu = computed(() => {
  return router.currentRoute.value.path
})

const toggleSidebar = () => {
  sidebarCollapse.value = !sidebarCollapse.value
}

const logout = () => {
  // 模拟退出登录
  ElMessage.success('退出登录成功')
  router.push('/login')
}
</script>

<style scoped>
.layout-container {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}

.layout-main {
  height: 100%;
}

.layout-sidebar {
  background-color: #001529;
  color: #fff;
  height: 100%;
  overflow-y: auto;
}

.sidebar-logo {
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: 1px solid #002140;
}

.sidebar-logo h2 {
  font-size: 18px;
  font-weight: bold;
}

.sidebar-menu {
  margin-top: 20px;
  background-color: transparent;
}

.sidebar-menu :deep(.el-menu-item) {
  color: rgba(255, 255, 255, 0.65);
  margin: 0 10px;
  border-radius: 6px;
}

.sidebar-menu :deep(.el-menu-item:hover) {
  color: #fff;
  background-color: rgba(255, 255, 255, 0.1);
}

.sidebar-menu :deep(.el-menu-item.is-active) {
  color: #fff;
  background-color: #1890ff;
}

.layout-header {
  height: 60px;
  background-color: #fff;
  border-bottom: 1px solid #e8e8e8;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 20px;
}

.header-left .el-button {
  margin-right: 20px;
}

.user-info {
  display: flex;
  align-items: center;
  cursor: pointer;
}

.user-info span {
  margin-left: 10px;
}

.layout-content {
  padding: 20px;
  overflow-y: auto;
}
</style>