<template>
  <div class="popup">
    <div class="addTask">
      <h2>Добавление новой задачи</h2>
      <form class="addTask__inner" @submit.prevent="addEvent">
        <div class="addTask__block">
          <input type="text" placeholder="Название задачи" id="taskName" autocomplete="off" required v-model="taskName">
          <input type="email" placeholder="Email" id="email" required v-model="taskEmail">
          <textarea placeholder="Описание задачи" id="taskText" cols="30" rows="10" required v-model="taskText"></textarea>
        </div>
        <div class="buttons">
          <button type="submit" id="createButton">
            <img src="@/assets/plus.png" alt="addTask">
            <span>Добавить</span>
          </button>
          <button type="button" id="close" @click="closeEvent">
            <span>Отмена</span>
          </button>
        </div>
      </form>
      <button class="closeButton" @click="closeEvent">
        <img src="@/assets/close-menu.png" alt="close">
      </button>
    </div>
  </div>
</template>

<script>

// const defaultVar = () => ({
//       taskName: null,
//       email:  null,
//       taskText: null,
//     });

export default {
  name: 'AddTask',
  data() {
    return this.defaultVar();
  },
  methods: {
    closeEvent() {
      this.$emit('close')
    },
    addEvent() {
      this.$emit('add', {
        taskName: this.taskName,
        taskEmail:  this.taskEmail,
        taskText: this.taskText,
      })
    },
    defaultVar (){
     return {
        taskName: null,
        taskEmail:  null,
        taskText: null,
      }
    } 
  },
}
</script>

<style scoped>
.popup {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
}
.addTask {
  padding-top: 25px;
  padding-right: 20px;
  padding-bottom: 25px;
  padding-left: 15px;
  background: rgba(88, 88, 88, 0.3);
  max-width: 400px;
  width: 100%;
  border-radius: 10px;
  box-shadow: 0px 0px 8px 3px rgba(88, 88, 88, 0.3);
  /* margin-bottom: 50px;  */
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  z-index: 10;}
  .addTask h2 {
    margin-bottom: 15px; }
  /* .addTask .addTask__inner {
    display: flex;
  } */
  .addTask .closeButton {
    position: absolute;
    top: 15px;
    right: 15px;
    width: 20px;
    height: 20px;
    cursor: pointer;
    transition: .3s;
    background: none;
    border: none;
  }
  .addTask .closeButton:hover img {
    filter:invert(0.2);
    transition: .3s;
  }
    .addTask .closeButton img {
      width: 100%;}
  .addTask .addTask__inner .addTask__block {
    display: flex;
    flex-direction: column;
  }
    .addTask .addTask__inner .addTask__block input, .addTask .addTask__block textarea {
      height: 40px;
      border: 1px solid #dddddd;
      border-radius: 10px;
      padding-left: 10px;
      max-width: 220px;
      width: 100%;
      transition: .3s;
      margin-bottom: 15px; }
      .addTask .addTask__inner .addTask__block input:hover, .addTask .addTask__block input:focus {
        box-shadow: 0px 0px 8px 3px rgba(206, 206, 206, 0.3);
        transition: .3s; }
    .addTask .addTask__inner .buttons {
      display: flex;
      justify-content: space-around; }
    .addTask .addTask__inner button {
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
      .addTask .addTask__inner button:hover {
        box-shadow: 0px 0px 8px 3px rgba(157, 162, 207, 0.418);
        background: #85a6b8;
        transition: .3s; }
      .addTask .addTask__inner button:focus {
        box-shadow: 0px 0px 8px 3px rgba(157, 162, 207, 0.418);
        transition: .3s; }
      .addTask .addTask__inner button span {
        margin-left: 10px;
        font-family: ProximaNova-Regular, sans-serif;
        font-size: 16px; }
</style>