<script setup>
import { ref } from 'vue';

const name = ref('Dagun Sultaev');
const status = ref('active');
const tasks = ref(['task1', 'task2', 'task3']);
const link = ref('https://google.com');
const newTask = ref('');

const toggleStatus = () => {
  if (status.value === 'active') {
    status.value = 'pending';
  } else if (status.value === 'pending') {
    status.value = 'inactive';
  } else {
    status.value = 'active';
  }
};

const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value);
    newTask.value = '';
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};
</script>

<template>
  <div>
    <h1>{{ name }}</h1>
    <p v-if="status === 'active'">User is active</p>
    <p v-else-if="status === 'pending'">User is still pending</p>
    <p v-else>User is inactive</p>

    <form @submit.prevent="addTask">
      <label for="newTask">Add task</label>
      <input type="text" id="newTask" name="newTask" v-model="newTask" />
      <button type="submit">Add</button>
    </form>

    <h3>Tasks:</h3>
    <ul>
      <li v-for="(task, index) in tasks" :key="task">
        <span>{{ task }}</span>
        <button @click="deleteTask(index)">x</button>
      </li>
    </ul>
    <a :href="link">google </a>

    <button @click="toggleStatus">Change status</button>
  </div>
</template>

<style></style>
