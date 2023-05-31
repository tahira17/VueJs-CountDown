<template>
  
  <div
  class="bg-blue-100 min-h-screen sm:p-10 p-5 flex flex-col justify-center dark:bg-[#0F172A] duration-500 transition-all ease-in-out">
  <Home />
</div>
</template>

<script>
import Home from './views/Home.vue'

export default {
  name: 'App',
  components: {
    Home
  }
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
</style>
