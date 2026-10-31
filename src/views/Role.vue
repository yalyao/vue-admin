<template>
  <div class="role-container">
    <h1 class="page-title">角色管理</h1>
    
    <div class="role-header">
      <el-button type="primary" @click="handleAddRole">新增角色</el-button>
    </div>
    
    <el-table :data="roles" style="width: 100%" class="role-table">
      <el-table-column prop="id" label="ID" width="80" />
      <el-table-column prop="name" label="角色名称" />
      <el-table-column prop="description" label="角色描述" />
      <el-table-column prop="createdTime" label="创建时间" width="180" />
      <el-table-column label="操作" width="180" fixed="right">
        <template #default="scope">
          <el-button type="primary" size="small" @click="handleEditRole(scope.row)" style="margin-right: 5px">
            编辑
          </el-button>
          <el-button type="danger" size="small" @click="handleDeleteRole(scope.row.id)">
            删除
          </el-button>
        </template>
      </el-table-column>
    </el-table>
    
    <el-dialog
      v-model="dialogVisible"
      :title="dialogTitle"
      width="500px"
    >
      <el-form :model="form" label-width="80px">
        <el-form-item label="角色名称">
          <el-input v-model="form.name" placeholder="请输入角色名称" />
        </el-form-item>
        <el-form-item label="角色描述">
          <el-input v-model="form.description" type="textarea" placeholder="请输入角色描述" rows="3" />
        </el-form-item>
      </el-form>
      <template #footer>
        <span>
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

const dialogVisible = ref(false)
const dialogType = ref('add')

const dialogTitle = computed(() => {
  return dialogType.value === 'add' ? '新增角色' : '编辑角色'
})

const form = reactive({
  id: '',
  name: '',
  description: ''
})

const roles = ref([
  {
    id: 1,
    name: '管理员',
    description: '系统管理员，拥有所有权限',
    createdTime: '2024-01-01 00:00:00'
  },
  {
    id: 2,
    name: '普通用户',
    description: '普通用户，拥有基本操作权限',
    createdTime: '2024-01-02 10:00:00'
  },
  {
    id: 3,
    name: '访客',
    description: '访客，拥有查看权限',
    createdTime: '2024-01-03 15:30:00'
  }
])

const handleAddRole = () => {
  dialogType.value = 'add'
  Object.assign(form, { id: '', name: '', description: '' })
  dialogVisible.value = true
}

const handleEditRole = (row) => {
  dialogType.value = 'edit'
  Object.assign(form, { ...row })
  dialogVisible.value = true
}

const handleSubmit = () => {
  if (dialogType.value === 'add') {
    const newRole = {
      id: roles.value.length + 1,
      ...form,
      createdTime: new Date().toLocaleString()
    }
    roles.value.push(newRole)
    ElMessage.success('新增角色成功')
  } else {
    const index = roles.value.findIndex(role => role.id === form.id)
    if (index !== -1) {
      roles.value[index] = { ...form }
      ElMessage.success('编辑角色成功')
    }
  }
  dialogVisible.value = false
}

const handleDeleteRole = (id) => {
  ElMessageBox.confirm('确定要删除这个角色吗？', '警告', {
    confirmButtonText: '确定',
    cancelButtonText: '取消',
    type: 'warning'
  }).then(() => {
    roles.value = roles.value.filter(role => role.id !== id)
    ElMessage.success('删除角色成功')
  }).catch(() => {})
}
</script>

<style scoped>
.role-container {
  width: 100%;
}

.page-title {
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 20px;
  color: #303133;
}

.role-header {
  margin-bottom: 20px;
}
</style>