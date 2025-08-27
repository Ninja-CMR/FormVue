<script setup>
import {defineModel , defineProps} from 'vue';
    name:  'InpuText'
   const modelValue = defineModel({type :String})
   const props = defineProps({
        placeholder : String , 
    }) ; 
</script>

<template>
    <div>
        <input 
        type="text" 
        :placeholder="placeholder" 
        :value = "modelValue"
        @input= "modelValue = $event.target.value"
        class="my-4  p-2 w-60 border-solid  border-2 border-gray-200 rounded-lg">
    </div>    
</template>