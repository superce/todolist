<template>
  <div class="inp_item">
    <div>
      <div class="todoItem">
        <input type="checkbox" class="checkbox" v-model="todo.completed">
        <span :class="['item',todo.completed ? 'completed' : '']">{{ todo.content }}</span>
        <input type="button" class="btn btn-info" value="✘" @click="delItem">
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Item',
    props:{
      todo:{
        type:Object,
        required:true
      }
    },
    methods: {
      delItem() {
        this.$emit('del',this.todo.id)
      }
    }
  }
</script>

<style scoped>
  .inp_item {
    margin: 0 40px;
  }

  .todoItem {
    overflow: hidden;
  }

  .todoItem .btn {
    float: right;
  }
  .todoItem span {
    color: #fff;
    font-size: 20px;
  }
  .todoItem .completed{
    text-decoration: line-through;
    color:#336666;
  }
</style>