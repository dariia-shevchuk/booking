<template>
  <div>
    <h1>User Details</h1>
    <div v-if="loading">Loading...</div>
    <div v-else-if="user">
      <p>Name: {{ user.name }}</p>
      <p>Email: {{ user.email }}</p>
    </div>
    <div v-else>
      User not found.
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      loading: true,
      user: null,
    };
  },
  mounted() {
    const email = 'theos.fa@gmail.com'; // Provide the email parameter

    axios.get(`http://localhost:3000/users/${email}`)
      .then(response => {
        this.loading = false;
        this.user = response.data;
      })
      .catch(error => {
        this.loading = false;
        console.error(error);
      });
  },
};
</script>
