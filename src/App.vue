<template>
  <div id="app">
    <div class="container">
        <h1>Todo application</h1>
        <hr>
        <router-view />
    </div>
    
  </div>
</template>

<script>

export default {
  name: 'App',

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container{
  max-width: 900px;
  min-width: 300px;
  margin: 0 auto;
}
</style>
