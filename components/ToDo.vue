<template>
  <div class="task-box">
    <h2 class="todo-header"> Your To Do List </h2>

    <button @click="clearTask" class="clear-tasks"> Clear To Do List </button>

    <div v-show="tasks.length">
      <div v-for="task in tasks" :key="task.id" class="todolist">

          <h3 class="name"> Task Name: {{ task.name }} </h3>
            <button @click="editNameShow">Edit Name</button>

            <div v-show="editTaskName">
              <input type="text" placeholder="New task name" v-model="newName">
              <button type="submit" @click="editName(task.id)"> Submit </button>
            </div>

          <h4 class="desc"> Description: {{ task.description }} </h4>
            <button @click="editDescShow">Edit Description</button>

              <div v-show="editTaskDescription">
                <input type="text" placeholder="New task description" v-model="newDesc">
                <button type="submit" @click="editDesc(task.id)"> Submit </button>
              </div>

            <button @click="deleteTask(task.id)">Delete</button>
            <button @click="completed(task)">Complete</button>
      </div>
    </div>
    <div v-show="!tasks.length" class="alt-t">
      <p> Your to do list is empty... </p>
      <p> Add some tasks! </p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['tasks'],
  data() {
    return {
      editTaskName: false,
      editTaskDescription: false,
      newName: '',
      newDesc: ''
    }
  },
  methods: {
    deleteTask(id) {
      this.$emit('delete', id)
    },
    clearTask() {
      this.$emit('clear')
    },
    completed(task) {
      this.$emit('completed', task)
    },
    editNameShow() {
      this.editTaskName = !this.editTaskName
    },
    editDescShow() {
      this.editTaskDescription = !this.editTaskDescription
    },
    editName(id) {
      this.$emit('editN', id, this.newName)
      this.newName = ''
      this.editTaskName = false
    },
    editDesc(id) {
      this.$emit('editD', id, this.newDesc)
      this.newDesc = ''
      this.editTaskDescription = false
    }
  }
}
</script>

<style scoped>
  .todo-header{
      margin: 5px;
      text-align: center;
      position: relative;
      height: auto 0;
      border-style:outset;
      width: fit-content;
      margin: 0 auto;
      padding: 10px;
      border-radius: 10px;
    }
  .task-box{
    background: #9bdfea;
    display: flex;
    flex-direction: column;
    padding: 10px;
    border-radius: 10px;
    margin: 10px;
    border-style: groove;
  }
  .name{
    margin: 5px;
    text-align: center;
    padding-top: 5px;
    padding-bottom: 5px;
  }
  .desc{
    margin: 5px;
    text-align: center;
    padding-top: 5px;
    padding-bottom: 5px;
  }
  .todolist{
    background: #Bec7cb;
    padding: 10px;
    border-radius: 10px;
    margin: 10px;
    border-style: groove;
  }
  .clear-tasks{
      max-width: fit-content;
      margin: 0 auto;
      padding-left: 10px;
      padding-right: 10px;      
  }
  .clear-tasks:hover {
    color:#A81212;
    border-style: solid;
    border-color: #A81212;
  }
  .alt-t{
    background: #Bec7cb;
    padding: 10px;
    border-radius: 10px;
    margin: 10px;
    border-style: groove;
  }
  button{
    margin: 2px;
  }
</style>