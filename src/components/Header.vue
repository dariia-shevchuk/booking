<script setup>
</script>

<template>
  <div class="nav search">
  <a href="/">Home</a>
  </div>
  <div class="nav login">
    <a href="#/login">Login</a>
  </div>
 <div class="nav sign-up">
    <a href="#/sign"> Sign up</a>
  </div>
  <div class="nav profile">
     <a href="#/profile">Profile</a>
  </div>
</template>

<script>
</script>


<style scoped>

span{
  cursor: pointer;
}
a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);

  }
a{
    padding:25px 30px;
    text-decoration: none;
    color: black;
    display:block;
  }
div.nav{
  display: flex;
  align-items:center;
  
  justify-content:center;

}
@media (min-width: 1024px) {

}
</style>