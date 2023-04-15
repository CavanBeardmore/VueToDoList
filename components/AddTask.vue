<template>
    <div class="addtask">
        <h2 class="add-header"> Add a new task </h2>

        <div>
            <label> Task Name: </label>
            <br>
            <input type="text" class="input1" placeholder="Task name is required" v-model="taskName" required>
        </div>

        <div>
            <label> Task Description: </label>
            <br>
            <input type="text" class="input2" placeholder="Task description is required" v-model="taskDescription" required>
        </div>

        <button @click="submitTask" class="buttonsubmit" :disabled="!taskName || !taskDescription"> Submit Task </button>

    </div>
</template>

<script>
export default {
    data() {
        return {
            taskName: '',
            taskDescription: '',
            id: 1,
            task: null
        }
    },
    methods: {
        submitTask() {
            this.task = { name: this.taskName, description: this.taskDescription, id: this.id ++ }
            this.taskName = ''
            this.taskDescription = ''
            this.$emit('add', this.task)
        }
    }
}
</script>

<style>
    .addtask{
        display: flex;
        flex-direction: column;
        background: #9bdfea;
        padding: 10px;
        border-radius: 10px;
        margin: 10px;
        border-style: groove;
    }
    .add-header{
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
    .input1{
        margin: 5px;
        text-align: center;
    }
    .input2{
        margin: 5px;
        text-align: center;
    }
    .buttonsubmit{
        margin: 5px;
        max-width: fit-content;
        margin: 0 auto;
    }
    .buttonsubmit:hover {
        color:#0D892C;
        border-style: solid;
        border-color: #0D892C;
    }
    .buttonsubmit:hover:disabled{
        color:#A81212;
        border-style: solid;
        border-color: #A81212;
    }
</style>