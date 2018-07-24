<template>
 <div class="home">
    <div class="title">
      <h1>todoList</h1>
    </div>
   <Todo/>
 </div>
</template>

<script>
import Todo from './Todo'

export default {
  components:{
    Todo    
  },
  name: 'Home'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .home{
    max-width: 1200px;
    margin: 0 auto;
  }
  .title{
    text-align: center;
    padding-top: 50px;
  }
</style>
