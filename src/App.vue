<script setup  >
import InpuText from './components/InputText.vue';
import InputNumber from './components/InputNumber.vue';
import InputRadio from './components/InputRadio.vue';
import ButtonComponent from './components/ButtonComponent.vue';
import InputEmail from './components/InputEmail.vue';
import Password from './components/Password.vue';
import { ref } from 'vue';
import { getSupportedCodeFixes } from 'typescript';


 const firstname = ref('') ;
 const sexe = ref ('') ; ; 
 const email = ref('') ; 
 const password = ref('') ;
 const isEmailValid = ref(false) ; 
 const isPasswordValid = ref(false)

const handleValidationEmail = (value)=>{
  isEmailValid.value = value ; 
}
const handleValidation = (value)=>{
 isPasswordValid.value = value ; 
}

 const GreetingValidation = ()=>{
  alert ('Thanks for you inscription')
 }



</script>
<template>
  <div>
      <div>
        <h1 class="text-6xl text-center font-bold text-sky-600  ">facebook</h1>
      </div>
      <div>
        <form @submit.prevent="submitForm" class="   bg-white pt-5 rounded-lg drop-shadow-md">
          <div 
          class="flex gap-3 justify-center items-center flex-col 
          w-full  border-b-2 border-gray-300 pb-3">
            <h2 class="text-2xl font-semibold">Create an account</h2>
            <p class="text-base text-gray-500">Is simple and easy</p>
          </div>
          <div class="flex flex-row  justify-center items-center gap-2 mx-6 ">
              <InpuText 
          v-model="firstname" 
           type ='text'
            placeholder = 'Firstname'
            />
               <InpuText 
          v-model="firstname" 
           type ='text'
            placeholder = 'Lastname'
            />
          </div>
          <div class="flex flex-col mx-5 ">
              <div>
                  <p class="text-sm mx-3 mb-3  ">Date de naissance</p>
              </div>
              <div class="  flex flex-row  justify-around items-center">
                  <InputNumber  placeholder="25" min ='1' max = '31' class="w-28"/>
                  <InputNumber  placeholder="5" min ='1' max = '12' class="w-28"/>
                  <InputNumber  placeholder="2025" min ='1990' max = '2001' class="w-28"/>
              </div>
          </div>

          <div class="flex flex-col m-5">
              <div>
                <p class="text-sm mx-5 ">Sexe</p>
              </div>
              <div class="flex justify-center gap-3 items-center mb-4">
                <InputRadio 
                      v-model="sexe"
                      name = 'sexe'
                      :options = "['Homme' , 'Femme']"
                />  
              </div>
        
              <div>
                  <InputEmail 
                  v-model="email"
                  placeholder = 'Email or phone number'
                  @isValid = "handleValidationEmail"
                    />
                    <Password :rules="{ minLength: 8 } " v-model:isValid="isPasswordValid"/>

              </div>
              <div class="mb-3">
                <p class="text-sm px-5 text-center">Les personnes qui utilisent notre service ont pu importer <br> vos coordonnées sur Facebook. <a href="" class="text-blue-400">En savoir plus</a>.</p>
              </div>
               <div class="flex flex-col justify-end items-center mb-4">
                  <ButtonComponent
                   :disabled="!isPasswordValid" 
                  @GreeTing = "GreetingValidation"
                  text = 'Inscrivez-vous'
                    />
               </div>
               <div class=" px-5 text-center mb-4 ">
                <a href="" class="text-lg text-blue-500 text-center">Avez-vous déjà un compte ?</a>
               </div>
          </div >
         
        </form>
      </div>
  </div>

</template>

