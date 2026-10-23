<script setup>
const records = [
  { id: 1, book: '《Vue3 实战》', user: '张三', borrowDate: '2026-10-01', dueDate: '2026-10-15', returned: false },
  { id: 2, book: '《JavaScript 高级程序设计》', user: '李四', borrowDate: '2026-10-12', dueDate: '2026-10-26', returned: false },
  { id: 3, book: '《深入浅出 Node.js》', user: '王五', borrowDate: '2026-09-20', dueDate: '2026-10-04', returned: true }
]
</script>

<template>
  <div class="card">
    <div class="card-head">
      <h2>📋 借阅记录</h2>
    </div>
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>书名</th>
          <th>借阅人</th>
          <th>借阅日期</th>
          <th>应还日期</th>
          <th>状态</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in records" :key="item.id">
          <td>{{ item.id }}</td>
          <td class="title">{{ item.book }}</td>
          <td>{{ item.user }}</td>
          <td>{{ item.borrowDate }}</td>
          <td>{{ item.dueDate }}</td>
          <td>
            <span :class="['tag', item.returned ? 'ok' : 'off']">
              {{ item.returned ? '已归还' : '借出中' }}
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
  padding: 20px 24px;
  border-bottom: 1px solid #f0f0f0;
}
.card-head h2 {
  margin: 0;
  color: #333;
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
  color: #409eff;
  background: rgba(64, 158, 255, 0.12);
}
</style>