<template>
  <div class="login-container">
    <h2>Login</h2>
    <form @submit="login" class="login-form">
      <input type="text" v-model="username" placeholder="Username/Email" required>
      <input type="password" v-model="password" placeholder="Password" required>
      <button type="submit">Login</button>
    </form>
    <p v-if="errorMessage" class="error-message">{{ errorMessage }}</p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      username: '',
      password: '',
      errorMessage: ''
    }
  },
  methods: {
    login(event) {
      event.preventDefault()
      axios.post('/api/login', {
        username: this.username,
        password: this.password
      })
      .then(response => {
        localStorage.setItem('token', response.data.token)
        this.$router.push('/dashboard')
      })
      .catch(error => {
        this.errorMessage = 'Invalid username/email or password'
        console.error(error)
      })
    }
  }
}
</script>

<style>
.login-container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
}

h2 {
  text-align: center;
  margin-bottom: 20px;
  color: #333;
}

.login-form {
  display: flex;
  flex-direction: column;
}

input {
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 10px 20px;
  background-color: #4682B4;
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 4px;
}

button:hover {
  background-color: #21637F;
}

.error-message {
  color: red;
  text-align: center;
}
</style>
