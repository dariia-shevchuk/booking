<template>
  <div class="logincont">
  <div class="login-container">
    <h2>Login</h2>
    <form @submit="login" class="login-form">
      <input type="text" v-model="username" placeholder="Username/Email" required>
      <input type="password" v-model="password" placeholder="Password" required>
      <button type="submit">Login</button>
    </form>
    <p v-if="errorMessage" class="error-message">{{ errorMessage }}</p>
  </div>
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
.logincont{
  height: 65vh;
  display: flex;
  align-items: center;
  /* background-color: #333; */
}

.login-container {
  width: 25%;
  margin: 0 auto;
  padding: 20px;
  background-color: #f5f5f5;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

h2 {
  text-align: center;
  margin-bottom: 20px;
  color: #333;
  font-size: 24px;
}

.login-form {
  display: flex;
  flex-direction: column;
}

input {
  margin-bottom: 10px;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
}

button {
  padding: 12px 24px;
  background-color: #4682B4;
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 4px;
  font-size: 16px;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #21637F;
}

.error-message {
  color: red;
  text-align: center;
  font-size: 14px;
}
</style>
