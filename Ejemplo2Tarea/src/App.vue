<script setup>
import { ref } from 'vue'
let newTask = ref('')
let taskList = ref([
  { text: 'Estudiar', done: false },
  { text: 'Jugar Play', done: true }
])

function addTask() {
  if (newTask.value.trim() === '') return
  taskList.value.push({
    text: newTask.value,
    done: false
  })
  newTask.value = ''
}

function setDone(index) {
  taskList.value[index].done = !taskList.value[index].done
}

function deleteTask(index) {
  taskList.value.splice(index, 1)
}
</script>

<template>
  <div class="card">
    <h1>Listas Cosas</h1>
    <p class="subtitle">{{ newTask }}</p>
    <div>
      <div v-for="(task, index) in taskList" :key="index" class="task" :class="{ done: task.done }">
        {{ task.text }}
        <span @dblclick="deleteTask(index)" @click="setDone(index)" class="button">x</span>
      </div>
    </div>
    <div>
      <input
        v-model="newTask"
        @keypress.enter="addTask"
        type="text"
        placeholder="Escribe tu tarea"
      />
      <p class="help" v-show="newTask != ''">Presiona ENTER para confirmar</p>
    </div>
  </div>
</template>

<style scoped>
.done {
  text-decoration: line-through;
  background-color: cadetblue !important;
}
.help {
  margin: 0;
  font-size: 13px;
  opacity: 0.4;
  text-align: center;
}
input {
  width: 100%;
  border: none;
  outline: none;
  padding: 6px;
  border-radius: 4px;
  box-sizing: border-box;
}
.button {
  background-color: #002333;
  color: white;
  padding: 0 5px;
  border-radius: 4px;
  justify-content: center;
}

.task:hover {
  background-color: #159a9c;
  color: white;
}
.task {
  display: flex;
  justify-content: space-between;
  background-color: #deefe7;
  border-radius: 4px;
  padding: 2px 8px;
  padding-right: 2px;
  padding-bottom: 2px;
  margin: 5px 0;
}
.subtitle {
  padding: 0;
  margin: 12px 0;
  text-align: center;
  opacity: 0.6;
}
h1 {
  text-transform: uppercase;
  text-align: center;
  padding: 0;
  margin: 0;
  font-size: 30px;
}
.card {
  background-color: #b4bec9;
  max-width: 350px;
  border-radius: 8px;
  padding: 18px 16px;
  margin: 0 auto;
  font-family: 'Oswald', sans-serif;
}
</style>
