<template>
  <div class="messages-page fade-in">
    <section class="page-banner">
      <div class="container">
        <h1>留言管理</h1>
        <p>共 {{ messages.length }} 条留言</p>
      </div>
    </section>

    <section class="messages-section">
      <div class="container">
        <div class="toolbar">
          <button class="btn btn-outline" @click="exportData" :disabled="messages.length === 0">导出数据</button>
          <button class="btn btn-danger" @click="clearAll" :disabled="messages.length === 0">清空所有</button>
        </div>

        <div class="messages-list" v-if="messages.length > 0">
          <div class="message-card" v-for="msg in messages" :key="msg.id">
            <div class="message-header">
              <div class="message-user">
                <span class="user-avatar">{{ msg.name.charAt(0) }}</span>
                <div>
                  <strong>{{ msg.name }}</strong>
                  <span class="message-time">{{ msg.time }}</span>
                </div>
              </div>
              <span class="message-type">{{ getTypeText(msg.type) }}</span>
            </div>
            <div class="message-body">
              <div class="message-info">
                <span>📞 {{ msg.phone }}</span>
                <span v-if="msg.email">📧 {{ msg.email }}</span>
                <span v-if="msg.company">🏢 {{ msg.company }}</span>
              </div>
              <p class="message-content">{{ msg.message }}</p>
            </div>
            <button class="delete-btn" @click="deleteMessage(msg.id)">删除</button>
          </div>
        </div>

        <div class="empty-state" v-else>
          <span class="empty-icon">📭</span>
          <p>暂无留言</p>
          <router-link to="/contact" class="btn btn-primary">去留言页</router-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const messages = ref([])

const loadMessages = () => {
  messages.value = JSON.parse(localStorage.getItem('contact_messages') || '[]')
}

const getTypeText = (type) => {
  const map = {
    website: '网站建设',
    miniapp: '小程序开发',
    data: '数据中台',
    ai: 'AI应用',
    other: '其他'
  }
  return map[type] || '未选择'
}

const deleteMessage = (id) => {
  if (confirm('确定要删除这条留言吗？')) {
    messages.value = messages.value.filter(m => m.id !== id)
    localStorage.setItem('contact_messages', JSON.stringify(messages.value))
  }
}

const clearAll = () => {
  if (confirm('确定要清空所有留言吗？此操作不可恢复！')) {
    messages.value = []
    localStorage.removeItem('contact_messages')
  }
}

const exportData = () => {
  const dataStr = JSON.stringify(messages.value, null, 2)
  const blob = new Blob([dataStr], { type: 'application/json' })
  const url = URL.createObjectURL(blob)
  const a = document.createElement('a')
  a.href = url
  a.download = `留言数据_${new Date().toLocaleDateString()}.json`
  a.click()
  URL.revokeObjectURL(url)
}

onMounted(() => {
  loadMessages()
})
</script>

<style scoped>
.page-banner {
  padding: 150px 0 80px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: #fff;
  text-align: center;
}

.page-banner h1 {
  font-size: 48px;
  margin-bottom: 12px;
}

.page-banner p {
  font-size: 18px;
  opacity: 0.9;
}

.messages-section {
  padding: 60px 0;
}

.toolbar {
  display: flex;
  gap: 12px;
  margin-bottom: 30px;
}

.btn-danger {
  background-color: #f56c6c;
  color: #fff;
}

.btn-danger:hover:not(:disabled) {
  background-color: #f78989;
}

.btn-danger:disabled {
  background-color: #fbc4c4;
  cursor: not-allowed;
}

.btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.messages-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.message-card {
  background-color: #fff;
  border: 1px solid #e4e7ed;
  border-radius: 12px;
  padding: 24px;
  transition: all 0.3s;
}

.message-card:hover {
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
}

.message-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}

.message-user {
  display: flex;
  align-items: center;
  gap: 12px;
}

.user-avatar {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: #fff;
  font-size: 20px;
  font-weight: 600;
  display: flex;
  align-items: center;
  justify-content: center;
}

.message-user strong {
  display: block;
  font-size: 16px;
  color: #303133;
}

.message-time {
  font-size: 13px;
  color: #909399;
}

.message-type {
  padding: 4px 12px;
  background-color: #ecf5ff;
  color: #409eff;
  font-size: 13px;
  border-radius: 4px;
}

.message-body {
  margin-bottom: 16px;
}

.message-info {
  display: flex;
  gap: 20px;
  margin-bottom: 12px;
  flex-wrap: wrap;
}

.message-info span {
  font-size: 14px;
  color: #606266;
}

.message-content {
  color: #303133;
  line-height: 1.8;
  background-color: #f8fafc;
  padding: 16px;
  border-radius: 8px;
  font-size: 14px;
}

.delete-btn {
  background: none;
  border: none;
  color: #f56c6c;
  font-size: 14px;
  cursor: pointer;
  padding: 4px 0;
}

.delete-btn:hover {
  text-decoration: underline;
}

.empty-state {
  text-align: center;
  padding: 80px 20px;
}

.empty-icon {
  font-size: 80px;
  display: block;
  margin-bottom: 16px;
}

.empty-state p {
  color: #909399;
  margin-bottom: 24px;
}
</style>