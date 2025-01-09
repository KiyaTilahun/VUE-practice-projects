<template lang="">
<div class="grid grid-cols-2 gap-4 w-full" >
 
  <!-- Form Section -->
  <div class="col-span-1">
    <form class="max-w-sm mx-auto"  @submit.prevent="addTask">
        <div class="mb-5">
  <label for="taskTime" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">
    Task Time
  </label>
  <input type="time" id="taskTime" 
         class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
         v-model="taskTime"
         required />
</div>
      <div class="mb-5">
        <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">
          Your New Task
        </label>
        <input type="text" id="email" 
               class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" 
               placeholder="new Task" v-model="newTask"
               required />
      </div>

      <button type="submit" 
              class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
        Submit
      </button>
    </form>
  </div>

  <!-- Table Section -->
  <div class="col-span-1">
    <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
      <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
        <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
          <tr>
            <th scope="col" class="px-6 py-3">
            No.
            </th>
            <th scope="col" class="px-6 py-3">
              Task name
            </th>
            <th scope="col" class="px-6 py-3">
              Task time
            </th>
            <th scope="col" class="px-6 py-3">
           
            </th>
          </tr>
        </thead>
        <tbody>

          <tr v-for="(task, index) in tasks" :key="index" class="odd:bg-white odd:dark:bg-gray-900 even:bg-gray-50 even:dark:bg-gray-800 border-b dark:border-gray-700">
            <td class="px-6 py-4">
              {{index+1}}
            </td>
            <td class="px-6 py-4">
              {{task.taskName}}
            </td>
            <td class="px-6 py-4">
              {{task.taskTime}}
            </td>
            <td class="px-6 py-4">
             
            
            <button v-on:click="deleteTask(index)"  type="button" class="focus:outline-none text-white bg-red-700 hover:bg-red-800 focus:ring-4 focus:ring-red-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-900">Delete Task</button>
        </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</div>

</template>
<script setup>
import { ref } from 'vue';

const newTask = ref('');
const taskTime = ref('');

const tasks = ref([]);

const addTask = () => {
    if (newTask.value.trim() != "") {
        tasks.value.push({   taskName: newTask.value,
            taskTime: taskTime.value})
    }
}
const deleteTask = (index) => {
    const confirmed = window.confirm('Are you sure you want to delete this task?');

    if (confirmed) {
        tasks.value.splice(index, 1);
        alert('Task deleted successfully!');
    }
};
</script>
<style lang="">

</style>