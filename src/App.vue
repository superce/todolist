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
body{
  height: 100%;
  background: url("./assets/1.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
  background-attachment: fixed;
  opacity: .7;
}

</style>
