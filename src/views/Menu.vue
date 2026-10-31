<template>
  <div class="menu-container">
    <h1 class="page-title">菜单管理</h1>
    
    <div class="menu-header">
      <el-button type="primary" @click="handleAddMenu">
        <el-icon><i-ep-plus /></el-icon>
        新增菜单
      </el-button>
    </div>
    
    <el-tree
      :data="menuList"
      :props="defaultProps"
      node-key="id"
      default-expand-all
      class="menu-tree"
    >
      <template #default="{ node, data }">
        <span class="menu-node">
          <span>{{ node.label }}</span>
          <span class="menu-actions">
            <el-button type="primary" size="small" @click.stop="handleEditMenu(data)" style="margin-right: 5px">
              编辑
            </el-button>
            <el-button type="danger" size="small" @click.stop="handleDeleteMenu(data.id)">
              删除
            </el-button>
          </span>
        </span>
      </template>
    </el-tree>
    
    <!-- 新增/编辑菜单对话框 -->
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
        <el-form-item label="菜单名称" prop="label">
          <el-input v-model="form.label" placeholder="请输入菜单名称" />
        </el-form-item>
        <el-form-item label="路由路径" prop="path">
          <el-input v-model="form.path" placeholder="请输入路由路径" />
        </el-form-item>
        <el-form-item label="图标" prop="icon">
          <el-input v-model="form.icon" placeholder="请输入图标名称" />
        </el-form-item>
        <el-form-item label="父菜单">
          <el-select v-model="form.parentId" placeholder="请选择父菜单">
            <el-option label="无（顶级菜单）" value="0" />
            <el-option
              v-for="menu in menuList"
              :key="menu.id"
              :label="menu.label"
              :value="menu.id"
            />
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

const dialogVisible = ref(false)
const dialogType = ref('add') // 'add' 或 'edit'
const formRef = ref(null)

const dialogTitle = computed(() => {
  return dialogType.value === 'add' ? '新增菜单' : '编辑菜单'
})

const form = reactive({
  id: '',
  label: '',
  path: '',
  icon: '',
  parentId: '0'
})

const rules = reactive({
  label: [
    { required: true, message: '请输入菜单名称', trigger: 'blur' }
  ],
  path: [
    { required: true, message: '请输入路由路径', trigger: 'blur' }
  ]
})

// 模拟菜单数据
const menuList = ref([
  {
    id: 1,
    label: '首页',
    path: '/dashboard',
    icon: 'Home',
    children: [
      {
        id: 11,
        label: '数据看板',
        path: '/dashboard',
        icon: 'DataAnalysis'
      }
    ]
  },
  {
    id: 2,
    label: '用户管理',
    path: '/user',
    icon: 'User',
    children: [
      {
        id: 21,
        label: '用户列表',
        path: '/user',
        icon: 'List'
      }
    ]
  },
  {
    id: 3,
    label: '角色管理',
    path: '/role',
    icon: 'Position',
    children: [
      {
        id: 31,
        label: '角色列表',
        path: '/role',
        icon: 'List'
      }
    ]
  },
  {
    id: 4,
    label: '菜单管理',
    path: '/menu',
    icon: 'Menu',
    children: [
      {
        id: 41,
        label: '菜单列表',
        path: '/menu',
        icon: 'List'
      }
    ]
  }
])

const defaultProps = {
  children: 'children',
  label: 'label'
}

const handleAddMenu = () => {
  dialogType.value = 'add'
  Object.assign(form, {
    id: '',
    label: '',
    path: '',
    icon: '',
    parentId: '0'
  })
  dialogVisible.value = true
}

const handleEditMenu = (data) => {
  dialogType.value = 'edit'
  Object.assign(form, { ...data })
  dialogVisible.value = true
}

const handleSubmit = async () => {
  if (!formRef.value) return
  
  await formRef.value.validate((valid, fields) => {
    if (valid) {
      if (dialogType.value === 'add') {
        // 新增菜单
        const newMenu = {
          id: getMaxId() + 1,
          ...form,
          children: []
        }
        if (form.parentId === '0') {
          // 顶级菜单
          menuList.value.push(newMenu)
        } else {
          // 子菜单
          const parentMenu = findMenuById(parseInt(form.parentId))
          if (parentMenu) {
            if (!parentMenu.children) {
              parentMenu.children = []
            }
            parentMenu.children.push(newMenu)
          }
        }
        ElMessage.success('新增菜单成功')
      } else {
        // 编辑菜单
        const menu = findMenuById(form.id)
        if (menu) {
          Object.assign(menu, { ...form })
          ElMessage.success('编辑菜单成功')
        }
      }
      dialogVisible.value = false
    }
  })
}

const handleDeleteMenu = (id) => {
  ElMessageBox.confirm('确定要删除这个菜单吗？', '警告', {
    confirmButtonText: '确定',
    cancelButtonText: '取消',
    type: 'warning'
  }).then(() => {
    // 删除菜单
    if (deleteMenuById(id)) {
      ElMessage.success('删除菜单成功')
    } else {
      ElMessage.error('删除菜单失败')
    }
  }).catch(() => {
    // 取消删除
  })
}

// 辅助函数：获取最大ID
const getMaxId = () => {
  let maxId = 0
  const traverse = (menus) => {
    menus.forEach(menu => {
      if (menu.id > maxId) {
        maxId = menu.id
      }
      if (menu.children && menu.children.length > 0) {
        traverse(menu.children)
      }
    })
  }
  traverse(menuList.value)
  return maxId
}

// 辅助函数：根据ID查找菜单
const findMenuById = (id, menus = menuList.value) => {
  for (const menu of menus) {
    if (menu.id === id) {
      return menu
    }
    if (menu.children && menu.children.length > 0) {
      const found = findMenuById(id, menu.children)
      if (found) {
        return found
      }
    }
  }
  return null
}

// 辅助函数：根据ID删除菜单
const deleteMenuById = (id, menus = menuList.value) => {
  for (let i = 0; i < menus.length; i++) {
    if (menus[i].id === id) {
      menus.splice(i, 1)
      return true
    }
    if (menus[i].children && menus[i].children.length > 0) {
      const deleted = deleteMenuById(id, menus[i].children)
      if (deleted) {
        return true
      }
    }
  }
  return false
}
</script>

<style scoped>
.menu-container {
  width: 100%;
}

.page-title {
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 20px;
  color: #303133;
}

.menu-header {
  margin-bottom: 20px;
}

.menu-tree {
  border: 1px solid #ebeef5;
  border-radius: 4px;
  padding: 10px;
}

.menu-node {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.menu-actions {
  visibility: hidden;
}

.menu-node:hover .menu-actions {
  visibility: visible;
}

.dialog-footer {
  display: flex;
  justify-content: flex-end;
}
</style>