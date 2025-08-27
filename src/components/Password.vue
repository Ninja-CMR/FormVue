<script setup>
import { ref, computed, defineEmits , watch } from 'vue'

const password = ref('')

// règles
const rules = {
  minLength: 8,
  hasUpperCase: /[A-Z]/,
  hasLowercase: /[a-z]/,
  hasNumber: /[0-9]/,
  hasSpecial: /[^A-Za-z0-9]/,
}

// validation
const validatePassword = computed(() => {
  return {
    minLength: password.value.length >= rules.minLength,
    hasUpperCase: rules.hasUpperCase.test(password.value),
    hasLowercase: rules.hasLowercase.test(password.value),
    hasNumber: rules.hasNumber.test(password.value),
    hasSpecial: rules.hasSpecial.test(password.value),
  }
})

// ✅ le mot de passe est valide si toutes les conditions passent
const isValid = computed(() => {
  const v = validatePassword.value
  return (
    v.minLength &&
    v.hasUpperCase &&
    v.hasLowercase &&
    v.hasNumber &&
    v.hasSpecial
  )
})

// on émet la validité au parent
const emit = defineEmits(['update:isValid'])
watch(password, () => {
  emit('update:isValid', isValid.value)
})
</script>

<template>
  <div class="mx-5 mb-2">
    <input
      type="password"
      v-model="password"
      placeholder="Password"
      class="px-3 py-2 w-full border-solid border-2 border-gray-200 rounded-lg mb-2"
    />

    <p class="text-xs">
      Minimum {{ rules.minLength }} caractères
      <span :class="validatePassword.minLength ? 'text-green-500' : 'text-red-500'">
        {{ validatePassword.minLength ? 'Valide' : 'Invalide' }}
      </span>
    </p>

    <p class="text-xs">
      Au moins une majuscule
      <span :class="validatePassword.hasUpperCase ? 'text-green-500' : 'text-red-500'">
        {{ validatePassword.hasUpperCase ? 'Valide' : 'Invalide' }}
      </span>
    </p>

    <p class="text-xs">
      Au moins une minuscule
      <span :class="validatePassword.hasLowercase ? 'text-green-500' : 'text-red-500'">
        {{ validatePassword.hasLowercase ? 'Valide' : 'Invalide' }}
      </span>
    </p>

    <p class="text-xs">
      Au moins un chiffre
      <span :class="validatePassword.hasNumber ? 'text-green-500' : 'text-red-500'">
        {{ validatePassword.hasNumber ? 'Valide' : 'Invalide' }}
      </span>
    </p>

    <p class="text-xs mb-2">
      Au moins un caractère spécial
      <span :class="validatePassword.hasSpecial ? 'text-green-500' : 'text-red-500'">
        {{ validatePassword.hasSpecial ? 'Valide' : 'Invalide' }}
      </span>
    </p>
  </div>
</template>
