<template>
<div>
  <div class="input">
    <input 
      type="text" 
      placeholder="请输入内容" 
      autofocus='autofocus' 
      class="inp form-control"
      @keyup.enter="addTodo"
    >
    <input type="button" value="提交" class="btn btn-danger">  
  </div> 
  <Item 
    :todo="todo"
    v-for="todo in todos"
    :key="todo.id"
    @del='delItem'
  />
   <Tabs :act="act"/>
</div>
</template>
  
<script>
import Item from './Item'
import Tabs from './Tabs'
let d = 0;
export default {
  components:{
    Item,
    Tabs
  },
  name: "Todo",
  data:() =>({
    todos:[],
    act:'all'
  }),
  methods:{
    addTodo(e){
      this.todos.unshift({
        id:d++,
        content:e.target.value.trim(),
        completed:false
      })
      e.target.value = ''
    },
    delItem(id){
      this.todos.splice(this.todos.findIndex(todo => todo.id == id),1)
    }
  }
};
</script>
 <style>
.input {
  padding: 50px 30px 0 30px;
  display: flex;
}
.inp {
  flex-grow: 1;
  height: 50px;
}
input {
  margin: 10px;
}
</style>
 
