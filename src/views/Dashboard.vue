<template>
  <div class="dashboard-container">
    <h1 class="page-title">首页</h1>
    
    <div class="stats-grid">
      <el-card class="stat-card">
        <div class="stat-content">
          <div class="stat-info">
            <div class="stat-number">1,234</div>
            <div class="stat-label" style="color: #409eff;">用户总数</div>
          </div>
        </div>
      </el-card>
      
      <el-card class="stat-card">
        <div class="stat-content">
          <div class="stat-info">
            <div class="stat-number">56</div>
            <div class="stat-label">今日新增</div>
          </div>
        </div>
      </el-card>
      
      <el-card class="stat-card">
        <div class="stat-content">
          <div class="stat-info">
            <div class="stat-number">89%</div>
            <div class="stat-label">活跃率</div>
          </div>
        </div>
      </el-card>
      
      <el-card class="stat-card">
        <div class="stat-content">
          <div class="stat-info">
            <div class="stat-number">23</div>
            <div class="stat-label">系统公告</div>
          </div>
        </div>
      </el-card>
    </div>
    
    <div class="recent-activity">
      <el-card>
        <template #header>
          <div class="card-header">
            <span>最近活动</span>
          </div>
        </template>
        <el-table :data="activityData" style="width: 100%">
          <el-table-column prop="time" label="时间" width="180" />
          <el-table-column prop="user" label="用户" width="120" />
          <el-table-column prop="action" label="操作" />
          <el-table-column prop="ip" label="IP地址" width="150" />
        </el-table>
      </el-card>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const activityData = ref([
  {
    time: '2024-01-18 10:30',
    user: 'admin',
    action: '登录系统',
    ip: '192.168.1.1'
  },
  {
    time: '2024-01-18 09:15',
    user: 'user1',
    action: '修改个人信息',
    ip: '192.168.1.2'
  },
  {
    time: '2024-01-18 08:45',
    user: 'admin',
    action: '添加新用户',
    ip: '192.168.1.1'
  },
  {
    time: '2024-01-17 16:20',
    user: 'user2',
    action: '查看数据报表',
    ip: '192.168.1.3'
  }
])
</script>

<style scoped>
.dashboard-container {
  width: 100%;
}

.page-title {
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 20px;
  color: #303133;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  margin-bottom: 20px;
}

.stat-card {
  height: 120px;
}

.stat-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100%;
}

.stat-info {
  flex: 1;
  display: flex;
  align-items: center;
  gap: 10px;
}

.stat-number {
  font-size: 24px;
  font-weight: bold;
  color: #f56c6c;
}

.stat-label {
  font-size: 14px;
  color: #f56c6c;
}

.recent-activity {
  margin-top: 20px;
}

.card-header {
  font-size: 16px;
  font-weight: bold;
  color: #303133;
}
</style>