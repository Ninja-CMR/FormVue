<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  text: String,
  disabled: Boolean,
})

const emit = defineEmits(['GreeTing'])
</script>

<template>
  <button
    @click="emit('GreeTing')"
    :disabled="disabled"
    class="px-3 py-2 rounded-lg font-bold text-center text-white"
    :class="disabled ? 'bg-gray-400 cursor-not-allowed' : 'bg-green-600 hover:bg-green-700'"
  >
    {{ text }}
  </button>
</template>
