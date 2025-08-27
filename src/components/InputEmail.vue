<script setup>
import {ref ,defineProps , defineModel , defineEmits ,  computed} from 'vue' ; 

const props = defineProps({
    placeholder : String , 

}) ; 
const modelValue = defineModel({type : String})

const emailRegex =/^[^\s@]+@[^\s@]+\.[^\s@]+$/

const isAValidEmail = computed(()=>{
    return emailRegex.test(modelValue.value || '');
});

const emits = defineEmits(['isValid']) ; 
const onInput = (e)=>{
    modelValue.value = e.target.value
    emits('isValid' , isAValidEmail.value) ; 
}
</script>

<template>
<div  class=" flex flex-col justify-center mx-5 mb-2"  >
    <input
    type="email"
    :value="modelValue"
    :placeholder="placeholder"
    @input="onInput"
    class="px-3 py-2 w-full border-solid border-2 border-gray-200 rounded-lg ">
     <p v-if="modelValue && isAValidEmail" 
     class="font-semibold text-green-500 text-left text-sm my-1 mb-3 ">
        Adresse Email valid 
    </p>
    <p v-if="modelValue && !isAValidEmail && modelValue.includes('@')"
     class="font-semibold text-left text-red-500 text-sm my-3">
        Adresse Email invalid 
    </p>
</div>

</template>