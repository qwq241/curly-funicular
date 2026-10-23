<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

function handleLogout() {
  localStorage.removeItem('library_token')
  router.replace('/login')
}
</script>

<template>
  <div class="layout">
    <!-- 侧边菜单 -->
    <aside class="sidebar">
      <h3>图书借阅系统</h3>
      <nav>
        <RouterLink to="/books">图书列表</RouterLink>
        <RouterLink to="/records">借阅记录</RouterLink>
      </nav>
      <button class="logout" @click="handleLogout">退出登录</button>
    </aside>
    <!-- 主内容区 -->
    <main class="content">
      <RouterView />
    </main>
  </div>
</template>

<style scoped>
.layout {
  display: flex;
  height: 100vh;
}

.sidebar {
  display: flex;
  flex-direction: column;
  gap: 16px;
  width: 200px;
  padding: 20px;
  color: #fff;
  background: #2c3e50;
}

/* 菜单项 */
.sidebar nav {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.sidebar a {
  color: #ecf0f1;
  text-decoration: none;
}

/* 当前激活菜单高亮 */
.sidebar a.router-link-active {
  color: #409eff;
  font-weight: bold;
}

.logout {
  margin-top: auto;
  padding: 8px;
  color: #fff;
  background: #e74c3c;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.content {
  flex: 1;
  padding: 24px;
  overflow: auto;
  background: #f5f7fa;
}
</style>