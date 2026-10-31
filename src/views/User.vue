<template>
  <div class="user-container">
    <h1 class="page-title">用户管理</h1>
    
    <div class="user-header">
      <el-input
        v-model="searchKeyword"
        placeholder="请输入用户名搜索"
        prefix-icon="Search"
        style="width: 300px; margin-right: 10px"
      />
      <el-button type="primary" @click="handleAddUser">
        <el-icon><i-ep-plus /></el-icon>
        新增用户
      </el-button>
    </div>
    
    <el-table :data="filteredUsers" style="width: 100%" class="user-table">
      <el-table-column prop="id" label="ID" width="80" />
      <el-table-column prop="username" label="用户名" />
      <el-table-column prop="email" label="邮箱" />
      <el-table-column prop="role" label="角色" />
      <el-table-column prop="status" label="状态" width="150">
        <template #default="scope">
          <div style="display: flex; align-items: center; gap: 8px;">
            <span class="status-label enable-label" :class="{ active: scope.row.status }">启用</span>
            <el-switch
              v-model="scope.row.status"
              @change="handleStatusChange(scope.row)"
            />
            <span :style="{ color: !scope.row.status ? '#f56c6c' : '#909399' }">禁用</span>
          </div>
        </template>
      </el-table-column>
      <el-table-column prop="createdTime" label="创建时间" width="180" />
      <el-table-column label="操作" width="180" fixed="right">
        <template #default="scope">
          <el-button type="primary" size="small" @click="handleEditUser(scope.row)" style="margin-right: 5px">
            编辑
          </el-button>
          <el-button type="danger" size="small" @click="handleDeleteUser(scope.row.id)">
            删除
          </el-button>
        </template>
      </el-table-column>
    </el-table>
    
    <div class="pagination-container">
      <el-pagination
        v-model:current-page="currentPage"
        v-model:page-size="pageSize"
        :page-sizes="[10, 20, 50, 100]"
        layout="total, sizes, prev, pager, next, jumper"
        :total="users.length"
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
      />
    </div>
    
    <!-- 新增/编辑用户对话框 -->
    <el-dialog
      v-model="dialogVisible"
      :title="dialogTitle"
      width="500px"
    >
      <el-form
        :model="form"
        :rules="rules"
        ref="formRef"
        label-width="80px"
      >
        <el-form-item label="用户名" prop="username">
          <el-input v-model="form.username" placeholder="请输入用户名" />
        </el-form-item>
        <el-form-item label="邮箱" prop="email">
          <el-input v-model="form.email" type="email" placeholder="请输入邮箱" />
        </el-form-item>
        <el-form-item label="密码" :prop="dialogType === 'add' ? 'password' : ''">
          <el-input
            v-model="form.password"
            type="password"
            placeholder="请输入密码"
            :disabled="dialogType === 'edit'"
          />
        </el-form-item>
        <el-form-item label="角色" prop="role">
          <el-select v-model="form.role" placeholder="请选择角色">
            <el-option label="管理员" value="admin" />
            <el-option label="普通用户" value="user" />
            <el-option label="访客" value="guest" />
          </el-select>
        </el-form-item>
      </el-form>
      <template #footer>
        <span class="dialog-footer">
          <el-button @click="dialogVisible = false">取消</el-button>
          <el-button type="primary" @click="handleSubmit">确定</el-button>
        </span>
      </template>
    </el-dialog>
  </div>
</template>

<script setup>
import { ref, reactive, computed } from 'vue'
import { ElMessage, ElMessageBox } from 'element-plus'

const searchKeyword = ref('')
const currentPage = ref(1)
const pageSize = ref(10)
const dialogVisible = ref(false)
const dialogType = ref('add') // 'add' 或 'edit'
const formRef = ref(null)

const dialogTitle = computed(() => {
  return dialogType.value === 'add' ? '新增用户' : '编辑用户'
})

const form = reactive({
  id: '',
  username: '',
  email: '',
  password: '',
  role: 'user',
  status: true
})

const rules = reactive({
  username: [
    { required: true, message: '请输入用户名', trigger: 'blur' }
  ],
  email: [
    { required: true, message: '请输入邮箱', trigger: 'blur' },
    { type: 'email', message: '请输入正确的邮箱格式', trigger: 'blur' }
  ],
  password: [
    { required: true, message: '请输入密码', trigger: 'blur' }
  ],
  role: [
    { required: true, message: '请选择角色', trigger: 'blur' }
  ]
})

// 模拟用户数据
const users = ref([
  {
    id: 1,
    username: 'admin',
    email: 'admin@example.com',
    role: 'admin',
    status: true,
    createdTime: '2024-01-01 00:00:00'
  },
  {
    id: 2,
    username: 'user1',
    email: 'user1@example.com',
    role: 'user',
    status: true,
    createdTime: '2024-01-02 10:00:00'
  },
  {
    id: 3,
    username: 'user2',
    email: 'user2@example.com',
    role: 'user',
    status: false,
    createdTime: '2024-01-03 15:30:00'
  },
  {
    id: 4,
    username: 'guest1',
    email: 'guest1@example.com',
    role: 'guest',
    status: true,
    createdTime: '2024-01-04 09:00:00'
  }
])

const filteredUsers = computed(() => {
  if (!searchKeyword.value) {
    return users.value
  }
  return users.value.filter(user => 
    user.username.toLowerCase().includes(searchKeyword.value.toLowerCase())
  )
})

const handleAddUser = () => {
  dialogType.value = 'add'
  Object.assign(form, {
    id: '',
    username: '',
    email: '',
    password: '',
    role: 'user',
    status: true
  })
  dialogVisible.value = true
}

const handleEditUser = (row) => {
  dialogType.value = 'edit'
  Object.assign(form, { ...row })
  dialogVisible.value = true
}

const handleSubmit = async () => {
  if (!formRef.value) return
  
  await formRef.value.validate((valid, fields) => {
    if (valid) {
      if (dialogType.value === 'add') {
        // 新增用户
        const newUser = {
          id: users.value.length + 1,
          ...form,
          createdTime: new Date().toLocaleString()
        }
        users.value.push(newUser)
        ElMessage.success('新增用户成功')
      } else {
        // 编辑用户
        const index = users.value.findIndex(user => user.id === form.id)
        if (index !== -1) {
          users.value[index] = { ...form }
          ElMessage.success('编辑用户成功')
        }
      }
      dialogVisible.value = false
    }
  })
}

const handleDeleteUser = (id) => {
  ElMessageBox.confirm('确定要删除这个用户吗？', '警告', {
    confirmButtonText: '确定',
    cancelButtonText: '取消',
    type: 'warning'
  }).then(() => {
    users.value = users.value.filter(user => user.id !== id)
    ElMessage.success('删除用户成功')
  }).catch(() => {
    // 取消删除
  })
}

const handleStatusChange = (row) => {
  ElMessage.success(`用户 ${row.username} 状态已更新为 ${row.status ? '启用' : '禁用'}`)
}

const handleSizeChange = (size) => {
  pageSize.value = size
  currentPage.value = 1
}

const handleCurrentChange = (current) => {
  currentPage.value = current
}
</script>

<style scoped>
.user-container {
  width: 100%;
}

.page-title {
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 20px;
  color: #303133;
}

.user-header {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.user-table {
  margin-bottom: 20px;
}

.pagination-container {
  display: flex;
  justify-content: flex-end;
}

.dialog-footer {
  display: flex;
  justify-content: flex-end;
}

.status-label {
  transition: color 0.3s;
}

.enable-label {
  color: #909399;
}

.enable-label.active {
  color: #409eff;
  animation: pulse-expand 2s ease-in-out infinite;
}

@keyframes pulse-expand {
  0% {
    transform: scale(1);
    text-shadow: 0 0 0 rgba(64, 158, 255, 0);
  }
  50% {
    transform: scale(1.3);
    text-shadow: 0 0 10px rgba(64, 158, 255, 0.6);
  }
  100% {
    transform: scale(1);
    text-shadow: 0 0 0 rgba(64, 158, 255, 0);
  }
}
</style>