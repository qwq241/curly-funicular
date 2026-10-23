<script setup>
import { useRouter } from 'vue-router'
import { useUserStore } from '@/stores/user'

const router = useRouter()
const userStore = useUserStore()

const books = [
  { id: 1, title: '《Vue3 实战》', author: '张三', available: true, count: 5 },
  { id: 2, title: '《JavaScript 高级程序设计》', author: 'Nicholas', available: false, count: 2 },
  { id: 3, title: '《深入浅出 Node.js》', author: '朴灵', available: true, count: 8 },
  { id: 4, title: '《CSS 揭秘》', author: 'Lea Verou', available: true, count: 3 }
]

function handleLogout() {
  userStore.logout()
  router.push('/login')
}
</script>

<template>
  <div class="card">
    <div class="card-head">
      <h2>📖 图书列表</h2>
      <button class="logout" @click="handleLogout">退出登录</button>
    </div>
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>书名</th>
          <th>作者</th>
          <th>库存</th>
          <th>状态</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="book in books" :key="book.id">
          <td>{{ book.id }}</td>
          <td class="title">{{ book.title }}</td>
          <td>{{ book.author }}</td>
          <td>{{ book.count }} 本</td>
          <td>
            <span :class="['tag', book.available ? 'ok' : 'off']">
              {{ book.available ? '可借' : '已借出' }}
            </span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.card {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
  overflow: hidden;
}
.card-head {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 24px;
  border-bottom: 1px solid #f0f0f0;
}
.card-head h2 {
  margin: 0;
  color: #333;
}
.logout {
  padding: 8px 16px;
  color: #e74c3c;
  background: rgba(231, 76, 60, 0.1);
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background 0.2s;
}
.logout:hover {
  background: rgba(231, 76, 60, 0.2);
}
table {
  width: 100%;
  border-collapse: collapse;
}
th,
td {
  padding: 14px 24px;
  text-align: left;
}
th {
  color: #666;
  font-size: 13px;
  font-weight: 500;
  background: #fafbfc;
}
td {
  color: #333;
  border-top: 1px solid #f0f0f0;
}
.title {
  font-weight: 500;
}
.tag {
  padding: 2px 10px;
  font-size: 12px;
  border-radius: 12px;
}
.tag.ok {
  color: #67c23a;
  background: rgba(103, 194, 58, 0.12);
}
.tag.off {
  color: #f56c6c;
  background: rgba(245, 108, 108, 0.12);
}
</style>