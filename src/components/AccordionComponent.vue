<template lang="">
<div  >
 
  
  <div v-for="item,index in data" :key="index" class="flex justify-center flex-col">
 
 
  <div class="border-b border-slate-200  ">
  <button v-on:click="toggleAccordion(index)" class="w-full flex justify-between items-center py-5 text-slate-800">
    <span>    {{item.title}}</span>
    <span id="icon-1" class="text-slate-800 transition-transform duration-300">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16" fill="currentColor" class="w-4 h-4">
        <path d="M8.75 3.75a.75.75 0 0 0-1.5 0v3.5h-3.5a.75.75 0 0 0 0 1.5h3.5v3.5a.75.75 0 0 0 1.5 0v-3.5h3.5a.75.75 0 0 0 0-1.5h-3.5v-3.5Z" />
      </svg>
    </span>
  </button>
 
  <div id="content-1" class="max-h-auto overflow-hidden  transition-all duration-300 ease-in-out" v-show="item.open" >
    <div class="pb-5 text-sm text-slate-500">
    {{item.detail}}
    </div>
  </div>
</div>
</div>

</div>

</template>
<script setup>
import { ref } from 'vue';
import axios from 'axios';

const data = ref([
  {
    title: "What is Vue.js?",
    detail: "Vue.js is a progressive JavaScript framework used for building user interfaces. It is designed to be incrementally adaptable."
    , open: false
  },
  {
    title: "How does the Virtual DOM work?",
    detail: "The Virtual DOM is a lightweight copy of the actual DOM. Vue uses it to optimize rendering by comparing changes before updating the real DOM."
    , open: false
  },
  {
    title: "What is a Vue directive?",
    detail: "Directives are special tokens in the markup that tell the library to do something to a DOM element, like `v-bind`, `v-for`, or `v-if`."
    , open: false
  },
  {
    title: "What are Vue components?",
    detail: "Components are reusable instances with their own data and logic. They help break the UI into smaller, manageable pieces."
    , open: false
  },
  {
    title: "What is Vue Router?",
    detail: "Vue Router is the official routing library for Vue.js, enabling navigation between different pages or components in a single-page application."
    , open: false
  },
]);

// 
const toggleAccordion = (index) => {
  console.log("hello");
  data.value = data.value.map((item, i) => ({
    ...item,
    open: i === index ? !item.open : false, // Close others and toggle the clicked one
  }));
};

</script>
<style lang="">

</style>