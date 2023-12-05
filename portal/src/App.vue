<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>

    <div class="wrapper">
      <h3>Portal</h3>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/abc">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style>
body {
  margin: 0;
}
.wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: black;
  color: #fff;
  padding: 0 32px;
}
nav a {
  margin-left: 10px;
  color: #fff;
}
</style>
