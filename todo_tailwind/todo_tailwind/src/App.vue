<script setup>
import TaskComponent from '@/components/TaskComponent.vue';

import{ref} from 'vue';
let tareas = ref([
'Comer', 'dormir', 'dormir'   
])  
</script>

<template>
<div class="px-4 py-2 w-96 bg-[#F2E3D5] shadow-md rounded mx-auto mt-10">
  <h1 class="text-2xl text-center font-semibold text-[#012E40]">Lista de Tareas</h1>

  <div class="flex mt-2">
    <input type="text" class="outline-none w-4/5 h-8 px-2 py-1 border border-[#012E40] rounded-r-none rounded">
    <span class="transition-colors duration-200 hover:cursor-pointer hover:bg-[#026773] rounded-l-none bg-[#024959]
     w-1/5 h-8 text-xl font-bold text-center text-white rounded"
     >+</span>
  </div>

  
<TaskComponent v-for="(tarea, index) in tareas"
:key="index"
:tarea = "tarea"
:index = "index"
/>



</div>
</template>

<style scoped>

</style>
