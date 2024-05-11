<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink :to="{ name: 'home' }">Home</RouterLink>
        |
        <RouterLink :to="{ name: 'about' }">About</RouterLink>
        |
        <RouterLink :to="{ name: 'jobs' }">Jobs</RouterLink>
      </nav>
    </div>
  </header>

  <button @click="redirect">Redirect</button>
  <button @click="back">Go back</button>
  <button @click="forward">Go forward</button>
  
  <RouterView />
</template>

<script>
import { RouterLink, RouterView } from 'vue-router'
export default {
  methods: {
    redirect() {
      this.$router.push({ name: 'home' })
    },
    back() {
      this.$router.go(-1)
    },
    forward() {
      this.$router.go(1)
    }
  }
}
</script>


<style>
  #app {
    text-align: center;
  }

  nav {
    padding: 30px;
  }

  nav a {
    font-weight: bold;
    text-decoration: none;
    color: #2c3e50;
    padding: 10px;
    border-radius: 10px;
  }

  nav a.router-link-exact-active {
    color: white;
    background: green;
  }
  
  button {
    margin: 0 10px;
    padding: 10px;
    border: none;
    border-radius: 4px;
  }
</style>
