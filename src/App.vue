<script setup>
import {ref, reactive} from "vue";

let tasks = reactive([]);
let task = ref('');

function addTask() {
    if (task.value.trim() !== '') {
        tasks.unshift(task.value)
        task.value = ''
    }
}

function deleteTask(index) {
    tasks.splice(index, 1)
}

</script>

<template>

    <div class="wrapper">
        <div class="card-box">

            <div class="input-row">
                <input v-model="task" type="text">
                <button @click="addTask">Add</button>
            </div>

            <hr>

            <div v-for="(task, index) in tasks" v-if="tasks.length > 0" class="task">
                <span>{{ task }}</span>
                <button @click="deleteTask(index)">🗑</button>
            </div>

        </div>
    </div>

</template>

<style>
html, body, #app {
    height: 100%;
    margin: 0;
}

.wrapper {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background: linear-gradient(135deg, #3f5efb, #5c6bc0);
}

.card-box {
    width: 600px;
    background: #f1f3f5;
    padding: 30px;
    border-radius: 18px;
    box-shadow: 0 15px 35px rgba(0,0,0,0.2);
}

.input-row {
    display: flex;
    margin-bottom: 25px;
}

.input-row input {
    flex: 1;
    padding: 12px;
    border-radius: 8px;
    border: 1px solid #ccc;
    font-size: 16px;
}

.input-row button {
    margin-left: 10px;
    padding: 12px 22px;
    border-radius: 8px;
    border: none;
    background: #3f5efb;
    color: white;
    cursor: pointer;
}

.task {
    background: #d9dee3;
    padding: 18px;
    border-radius: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 15px;
}

.task button {
    width: 40px;
    height: 40px;
    border-radius: 8px;
    border: none;
    background: #3f5efb;
    color: white;
    cursor: pointer;
}
</style>

