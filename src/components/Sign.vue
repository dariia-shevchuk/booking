<template>
  <div class="register-container">
    <h2 class="register-title">Register</h2>
    <form @submit="register" class="register-form">
      <input type="text" v-model="username" placeholder="Username" class="register-input" required>
      <input type="email" v-model="email" placeholder="Email" class="register-input" required>
      <input type="password" v-model="password" placeholder="Password" class="register-input" required>
      <button type="submit" class="register-button">Register</button>
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
      email: '',
      password: '',
      errorMessage: ''
    }
  },
  methods: {
    register(event) {
      event.preventDefault()
      axios.post('/api/register', {
        username: this.username,
        email: this.email,
        password: this.password
      })
      .then(response => {
        console.log('Registration successful:', response.data)
        this.$router.push('/login')
      })
      .catch(error => {
        this.errorMessage = 'Registration failed. Please try again.'
        console.error(error)
      })
    }
  }
}
</script>

<style>
.register-container {

  max-width: 400px;
  
  margin: 0 auto;
  padding: 20px;
  //background-color: #f5f5f5;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.register-title {
  text-align: center;
  margin-bottom: 20px;
  color: #333;
  font-size: 24px;
}

.register-form {
  display: flex;
  flex-direction: column;
}

.register-input {
  margin-bottom: 10px;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
}

.register-button {
  padding: 12px 24px;
  background-color: #4682B4;
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 4px;
  font-size: 16px;
  transition: background-color 0.3s;
}

.register-button:hover {
  background-color: #21637F;
}

.error-message {
  color: red;
  text-align: center;
  font-size: 14px;
}
</style>
