<template>
  <nav class="main-nav">
    <router-link :to="{ name: 'home' }">Projects</router-link> |
    <router-link :to="{ name: 'addProject' }">Add Project</router-link>
  </nav>
</template>

<script>
export default {};
</script>

<style>
.main-nav {
  padding: 30px;
  text-align: center;
  font-size: 22px;
}
.main-nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
}
.main-nav a.router-link-exact-active {
  color: white;
  border-radius: 5px;
  color: #42b983;
}
</style>