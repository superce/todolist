<template>
  <div>
    <div class="input">
      <input type="text" placeholder="请输入内容" autofocus='autofocus' class="inp form-control" @keyup.enter="addTodo">
    </div>
    <div class="item_box">
      <Item :todo="todo" v-for="todo in filted" :key="todo.id" @del='delItem' />
    </div>
    <Tabs :act="act" :todos='todos' @toggle='toggle' @clear="cleatCompleted" />
  </div>
</template>

<script>
  import Item from './Item'
  import Tabs from './Tabs'
  let d = 0;
  export default {
    components: {
      Item,
      Tabs
    },
    name: "Todo",
    data: () => ({
      todos: [],
      act: 'all'
    }),
    computed: {
      filted() {
        if (this.act == 'all') {
          return this.todos
        }
        const completed = this.act == 'completed'
        return this.todos.filter(todo => completed == todo.completed)
      }
    },
    methods: {
      addTodo(e) {
        this.todos.unshift({
          id: d++,
          content: e.target.value.trim(),
          completed: false
        })
        e.target.value = ''
      },
      delItem(id) {
        this.todos.splice(this.todos.findIndex(todo => todo.id == id), 1)
      },
      toggle(tab) {
        this.act = tab
      },
      cleatCompleted(todo) {
        this.todos = this.todos.filter(todo => !todo.completed)
      }
    }
  };
</script>
<style>
  .input {
    padding: 50px 30px 0 30px;
    display: flex;
  }
  .item_box{
    min-height: 300px;
  }
  .inp {
    flex-grow: 1;
    height: 50px;
  }

  input {
    margin: 10px;
  }
</style>