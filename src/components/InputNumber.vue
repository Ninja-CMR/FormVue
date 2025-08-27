<script setup>
import { defineProps , defineModel } from 'vue';
const props = defineProps({ 
   placeholder :{type : String , default : ''},
   max : String,
   min : String
}) ; 
const modelValue = defineModel({
 type : String
})

</script>

<template>
 
 <input 
 :value="modelValue" 
 type="number"
 :placeholder="placeholder" 
 :min = 'min'
 :max = 'max'
 @input= "modelValue = $event.target.value"
 class="px-3 py-2 w-36 border-solid border-2 border-gray-200 rounded-lg">
</template>