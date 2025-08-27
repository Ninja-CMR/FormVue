<script setup>
import { defineProps,  defineModel, ref } from 'vue';
const props = defineProps({
   options : {type : Array, required: true } , 
   label : String , 
    name : String , 
})
const modelValue = defineModel({type : String})

</script>

<template>
    <div v-for="option in options" :key="option" class="flex flex-row gap-3  justify-center items-center 
    border-2 border-gray-200 ppx-3 py-2 w-36 rounded-lg ">
      <label v-if="label" for="">{{ label }}</label> 
      <label>{{ option }}</label>
     <input 
       :value='option'
       :name = "name"
        type = 'radio'
        v-model="modelValue"> 
    </div>
</template>