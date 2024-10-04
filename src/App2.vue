<script>
export default {
  data() {
    return {
      name: 'Dagun Sultaev',
      status: 'active',
      tasks: ['task1', 'task2', 'task3'],
      link: 'https://google.com',
    };
  },

  methods: {
    toggleStatus() {
      if (this.status === 'active') {
        this.status = 'pending';
      } else if (this.status === 'pending') {
        this.status = 'inactive';
      } else {
        this.status = 'active';
      }
    },
  },
};
</script>

<template>
  <div>
    <h1>{{ name }}</h1>
    <p v-if="status === 'active'">User is active</p>
    <p v-else-if="status === 'pending'">User is still pending</p>
    <p v-else>User is inactive</p>

    <h3>Tasks:</h3>
    <ul>
      <li v-for="task in tasks" :key="task">{{ task }}</li>
    </ul>
    <a :href="link">google </a>

    <button @click="toggleStatus">Change status</button>
  </div>
</template>

<style></style>
