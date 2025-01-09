<template lang="">
<div class="grid grid-cols-1 gap-4 " >
 
  
<a href="#" class="block max-w-sm p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700 w-screen">

<h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">Todays Quote</h5>
<p class="font-normal text-gray-700 dark:text-gray-400">"{{myquotes}}"</p>
<button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" v-on:click="getRandom">Get new Quote</button>

</a>

</div>

</template>
<script setup>
import { ref } from 'vue';
import axios from 'axios';

const myquotes = ref('--------');

const getRandom = async () => {
  try {
    const min = 1;
const max = 10;
const randomNumber = Math.ceil(Math.random() * (max - min) + min);
 
    
    const response = await axios.get(`https://dummyjson.com/quotes/${randomNumber}`); // Replace with your API endpoint
    myquotes.value=response.data.quote; 
  } catch (error) {
    console.error('Error fetching random data:', error);
    throw error; 
  }
};



</script>
<style lang="">

</style>