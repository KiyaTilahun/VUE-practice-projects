<template>

    
  <form v-on:submit.prevent="">
    <div class="mb-6">
        <label for="success" class="block mb-2 text-sm font-medium text-green-700 dark:text-green-500">Your name</label>
        <input type="text" id="success"
            class="bg-green-50 border border-green-500 text-green-900 dark:text-green-400 placeholder-green-700 dark:placeholder-green-500 text-sm rounded-lg focus:ring-green-500 focus:border-green-500 block w-full p-2.5 dark:bg-gray-700 dark:border-green-500"
            placeholder="Password input"    v-model="pass" >
        <p class="mt-2 text-sm text-green-600 dark:text-green-500"><span class="font-medium">Well done!</span> Some
            success message.</p>
    </div>
  </form>
  <button v-on:click="createPass" class="text-blue-700 hover:text-white border border-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center me-2 mb-2 dark:border-blue-500 dark:text-blue-500 dark:hover:text-white dark:hover:bg-blue-500 dark:focus:ring-blue-800">Create Random Password</button>

</template>
<script setup>
import { ref } from 'vue';
const  pass=ref('');
const createPass = () => {
  const length = 12; 
  const charset = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_+[]{}|;:,.<>?'; // Characters to include in the password
  let generatedPass = '';
  for (let i = 0; i < length; i++) {
    const randomIndex = Math.floor(Math.random() * charset.length);
    generatedPass += charset[randomIndex];
  }
  pass.value = generatedPass; // Update the reactive password value
};
</script>
<style lang="">

</style>