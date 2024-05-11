<template>
  <h1>The Jobs Page</h1>
  <div v-if="jobs.length">
    <div class="job" v-for="job in jobs" :key="job.id">
      <RouterLink :to="{ name: 'jobDetails', params: { id: job.id } }">
        <h2>{{ job.title }}</h2>
      </RouterLink>
    </div>
  </div>
  <div v-else>
    <p>loading...</p>
  </div>
</template>

<script>
import { RouterLink } from 'vue-router';
export default {
  data () {
    return {
      jobs: [] 
    }
  },
  mounted() {
    fetch('http://localhost:3000/jobs')
      .then(res => res.json())
      .then(data => this.jobs = data)
      .catch(err => console.log(err.message))
  }
}
</script>

<style>
  .job h2 {
    background: rgb(231, 228, 228);
    padding: 15px;
    max-width: 500px;
    margin: 10px auto;
    border-radius: 6px;
    cursor: pointer;
    color: #444;
  }
  .job a {
    text-decoration: none;
  }
  .job h2:hover {
    background: #ddd;
  }
</style>