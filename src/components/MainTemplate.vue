<template>
  <div class="template">
    <header class="header">
      <h1 class="title">Список задач</h1>
      <button type="button" id="createButton" @click="showPopup = true">
        <img src="@/assets/plus.png" alt="addTask">
        <span>Создать новую задачу</span>
      </button>
    </header>
    <div class="container">
      <AddTask v-if="showPopup" @close="showPopup = false" @add="addNewTask"/>
      <TaskList :tasks="taskList" @delete-task="deleteTask"/>
    </div>
  </div>
</template>

<script>
import AddTask from '@/components/AddTask.vue'
import TaskList from '@/components/TaskList.vue'

export default {
  name: 'MainTemplate',
  components: {
    AddTask,
    TaskList
  },
   data() {
    return {
      showPopup: false,
      taskList: [],
    };
  },
  methods: {
    addNewTask(evt) {
      this.taskList.push(evt);
      console.log(this.taskList);
      this.showPopup = false;
    },
    deleteTask(evt) {
      //console.log(evt);
      this.taskList.splice(evt, 1);
      console.log(this.taskList);
    }
  }
}
</script>

<style scoped>
.template .header {
  padding: 10px 0;
  margin-bottom: 60px;
  background: rgba(88, 88, 88, 0.3);
  box-shadow: 0px 0px 8px 3px rgba(88, 88, 88, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;}
  .header h1 {
    margin: 0;
    margin-right: 50px;
    font-size: 40px;
  }
  .header button {
    height: 40px;
    border: 1px solid #667e8b;
    border-radius: 10px;
    padding: 0 15px;
    cursor: pointer;
    background: #667e8b;
    color: #ffffff;
    transition: .3s;
    display: flex;
    align-items: center; }
    .header button:hover {
      box-shadow: 0px 0px 8px 3px rgba(157, 162, 207, 0.418);
      background: #85a6b8;
      transition: .3s; }
    .header button:focus {
      box-shadow: 0px 0px 8px 3px rgba(157, 162, 207, 0.418);
      transition: .3s; }
    .header button span {
      margin-left: 10px;
      font-family: ProximaNova-Regular, sans-serif;
      font-size: 16px; }
</style>