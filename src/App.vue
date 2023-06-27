<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import { ref, computed } from 'vue'
import Home from './components/Home.vue'
import Login from './components/Login.vue'
import Sign from './components/Sign.vue'
import Profile from './components/Profile.vue'

const routes = {
  '/': Home,
  '/login': Login,
  '/sign': Sign,
  '/profile': Profile
}

const currentPath = ref(window.location.hash)

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || '/'] || NotFound
})
</script>

<template>
  <div class="header">
    <Header/>
  </div>
  <div class="app">
    <component :is="currentView" />
  </div>
  <div class="footer">
    <Footer/>
  </div>
</template>

<style scoped>
.header{
  height: 75px;
  background: rgb(70, 145, 168);
  display: flex;
  flex-flow: row wrap;
  justify-content: flex-end;
}
.footer{
  height: 300px;
  display: block;
  background: rgb(1, 99, 210);
}
.app{
  min-height: 1000px; 
    background: white;
  }
</style>
