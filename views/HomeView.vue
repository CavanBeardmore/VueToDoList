<template>
  <h1 class="heading"> To Do List </h1>
  <div class="home">
    <AddTask @add="changeTasks" class="add-box" />
    <ToDo :tasks="taskList" @delete="deleteTask" @clear="clearTask" @completed="completed" @editN="editName" @editD="editDesc" class="todo-box" />
    <Completed :completeList="completedTasks" @clearC="clearCompleted" class="completed-box" />
  </div>
</template>

<script>
import AddTask from '../components/AddTask.vue'
import ToDo from '../components/ToDo.vue'
import Completed from '../components/Completed.vue'

export default {
  name: 'HomeView',
  components: { 
    AddTask,
    ToDo,
    Completed 
    },
  data() {
    return {
      taskList: [],
      completedTasks: []
    }
  },
  methods: {
    changeTasks(task) {
      this.taskList = this.taskList.concat(task)
    },
    deleteTask(id) {
      this.taskList = this.taskList.filter((task) => task.id !== id)
    },
    clearTask() {
      this.taskList = []
    },
    completed(task) {
      this.completedTasks = this.completedTasks.concat(task)
      this.taskList = this.taskList.filter((taskValue) => taskValue.id !== task.id)
    },
    clearCompleted() {
      this.completedTasks = []
    },
    editName(id, newValue) {
      const task = this.taskList.find( task => task.id === id)
      if (task) {
        task.name = newValue
      }
    },
    editDesc(id, newValue) {
      const task = this.taskList.find( task => task.id === id)
      if (task) {
        task.description = newValue
      }
    }
  }
}
</script>

<style>
    .home{
        display: flex;
        flex-direction: row;
        background: #Dee2df;
        height: 90%;
        flex-wrap: wrap;
    }
    .add-box{
        text-align: center;
        justify-content: space-evenly;
        flex-grow: 1;
        padding-right: 15px;
    }
    .todo-box{
        text-align: center;
        justify-content: space-evenly;
        flex-grow: 1;
        padding-right: 15px;
        padding-left: 15px;
    }
    .completed-box{
        text-align: center;
        justify-content: space-evenly;
        flex-grow: 1;
        padding-left: 15px;
    }
    .heading{
      background: #9bdfea;
      padding: 10px;
      border-radius: 10px;
      margin: 0 auto;
      max-width: fit-content;
      border-style: groove
    }
</style>