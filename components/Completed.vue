<template>
  <div class="completed-header">
    <h2 class="comp-header"> Completed Tasks </h2>
    <button @click="clearCompleted" class="clear-comp"> Clear Completed Tasks </button>
    <div v-show="completeList.length">
      <div v-for="task in completeList" :key="task.id" class="completed-tasks">
        <h3 class="c-name"> Task Name: {{ task.name }} </h3>
        <h4 class="c-desc"> Description: {{ task.description }} </h4>
      </div>
    </div>
    <div v-show="!completeList.length" class="alt-c">
      <p> You haven't completed any tasks yet... </p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['completeList'],
  methods: {
    clearCompleted() {
      this.$emit('clearC')
    }
  }
}
</script>

<style>
  .comp-header{
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
  .completed-header{
    display: flex;
    flex-direction: column;
    background: #9bdfea;
    padding: 10px;
    border-radius: 10px;
    margin: 10px;
    border-style: groove;
  }
  .c-name{
    margin: 5px;
    text-align: center;
    color:#1a9410;
  }
  .c-desc{
    margin: 5px;
    text-align: center;
    color: #1a9410;
  }
  .completed-tasks{
    background: #Bec7cb;
    padding: 10px;
    border-radius: 10px;
    margin: 10px;
    border-style: groove;
  }
  .clear-comp{
    max-width: fit-content;
    margin: 0 auto;
    padding-left: 10px;
    padding-right: 10px;
  }
  .clear-comp:hover {
    color:#A81212;
    border-style: solid;
    border-color: #A81212;
  }
  .alt-c{
    background: #Bec7cb;
    padding: 10px;
    border-radius: 10px;
    margin: 10px;
    border-style: groove;
  }
</style>