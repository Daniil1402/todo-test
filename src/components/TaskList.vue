<template>
  <table class="taskList">
    <tr>
      <th>Номер</th>
      <th>Email</th>
      <th>Название задачи</th>
      <th>Описание задачи</th>
      <th>Удалить задачу</th>
      </tr>
    <tr v-for="(task, idx) in tasks" :key="idx">
      <td>{{idx + 1}}</td>
      <td>{{task.taskEmail}}</td>
      <td>{{task.taskName}}</td>
      <td>{{task.taskText}}</td>
      <td><img src="@/assets/close-menu.png" alt="delete" @click="deleteTask(idx)"></td>
    </tr>
  </table>
</template>

<script>

export default {
  name: 'TaskList',
  props: {
    tasks: Array,
  },
  methods: {
    deleteTask(idx) {
      this.$emit('delete-task', {
        idx: idx,
      })
    },
  }
}
</script>

<style scoped>
  .taskList {
    width: 100%;
  }
  table {
   border: 1px solid rgb(255, 255, 255);
   border-collapse: collapse;
  }
  th {
   border: 1px solid rgb(255, 255, 255);
   text-align: center;
   padding: 15px 0;
  }
  td {
    border: 1px solid rgb(255, 255, 255);
    text-align: center;
    padding: 15px 0;
    cursor: pointer;
  }
   tr:hover td {
    background: #85a6b8;
  }
</style>