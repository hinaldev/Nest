<template>
  <div id="app">
    <h1 class="title">Users List</h1>
    <ul class="user-list">
      <li v-for="user in users" :key="user.id" class="user-item">
        <div class="user-card">
          <h3 class="user-name">{{ user.name }}</h3>
          <p class="user-email">{{ user.email }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      users: []
    };
  },
  mounted() {
    fetch('http://localhost:3000/users')
      .then(response => response.json())
      .then(data => {
        this.users = data;
      })
      .catch(error => console.log(error));
  }
};
</script>

<style src="./assets/styles.css"></style>
