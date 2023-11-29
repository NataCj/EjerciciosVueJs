<script setup>
const props = defineProps(
    {
        tarea:{
            type: String
            default: 'Tarea por defecto'
        },
        index:{
            type: Number
            
        }
    }
)
</script>

<template>
    <div class="flex justify-between text-white bg-[#026773] px-4 py-1 mt-1">
    Tarea 1
    <span class="transition-colors duration-200 hover:cursor-pointer hover:bg-[#026773]  px-3 py-1 text-center text-white rounded">X</span>
  </div>
</template>