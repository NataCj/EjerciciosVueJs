<script setup>
import { ref } from 'vue'
let newTask = ref('')
let taskList = ref([
  {
    name: 'Estudiar',
    done: false
  },
  {
    name: 'comer',
    done: false
  },
  {
    name: 'dormir',
    done: false
  }
])

function deleteTalk(index) {
  taskList.value.splice(index, 1)
}
function addTask() {
  if (newTask.value.trim() === '') return
  taskList.value.push({
    name: newTask.value,
    done: false
  })
  newTask.value = ''
}

function setDone(index) {
  taskList.value[index].done = !taskList.value[index].done
}
</script>

<template>
  <div class="container">
    <h1>Lista de Tareas</h1>
    <p class="subtitle">{{ newTask }}</p>

    <div>
      <div class="task" :class="{ done: task.done }" v-for="(task, index) in taskList" :key="index">
        {{ task.name }}
        <span @dblclick="deleteTalk(index)" @click="setDone(index)" class="button">X</span>
      </div>
    </div>

    <input v-model="newTask" @keypress.enter="addTask" type="text" placeholder="Escriba su tarea" />
    <p v-show="newTask != ''" class="help">Presiona enter para agregar la tarea</p>
  </div>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
.help {
  font-size: 10px;
  margin: 0;
  opacity: 0.6;
  text-align: center;
}
.container {
  color: #012030;
  padding: 6px 12px;
  font-family: 'Anton', sans-serif;
  background-color: #13678a;
  border-radius: 8px;
  max-width: 420px;
  margin: 0 auto;
}

.task {
  background-color: #45c4b0;
  border-radius: 3px;
  margin-bottom: 1px;
  padding: 2px 2px 1px 6px;
  display: flex;
  justify-content: space-between;
}

input {
  border: none;
  border-radius: 3px;
  padding: 2px 6px;
  outline: none;
  /*width: calc(100% - 12px);*/
  box-sizing: border-box;
  width: 100%;
  background-color: #9aeba3;
  margin-top: 12px;
}

input::placeholder {
  opacity: 0.4;
  color: #012030;
}
.task:hover {
  background-color: rgb(93, 255, 231, 0.8);
}
.subtitle {
  font-size: 13px;
  margin: 0;
  margin-bottom: 16px;
  text-align: center;
  opacity: 0.6;
}

.button {
  background-color: #9aeba3;
  display: inline-block;
  padding: 0 6px;
  border-radius: 3px;
  cursor: pointer;
}

h1 {
  text-transform: uppercase;
  font-size: 32px;
  text-align: center;
  margin: 0;
  margin-top: 12px;
}
</style>
