<template>
  <div id="app">
    <Home/>
  </div>
</template>

<script>
import Home from '@/components/Home.vue'
export default {
  components:{
    Home
  },
  name: 'App'
}
</script>

<style>
*{
  margin: 0;padding: 0;
}
#app{
  height: 100vh;
  background: url("./assets/1.jpg") no-repeat;
  background-size: cover;
  opacity: .7;
}
</style>
