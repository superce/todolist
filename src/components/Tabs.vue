<template>
  <div class="footer">
    <div class="tab_left">
      <span>
        {{ itemsLength }}item
      </span>
    </div>
    <div class="tab_content">
      <span 
        v-for="tab in tabs" :key="tab" 
        :class="[tab,act === tab ? 'actived' : '']"
        @click="toggle(tab)"
      >
        {{ tab }}
      </span>
    </div>
    <div class="tab_right">
      <span @click="clearCompleted">
        clear completed
      </span>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Tabs',
    props:{
      act:{
        type:String,
        required: true
      },
      todos:{
        type:Array,
        required:true
      }
    },
    data:() => ({
      tabs:[
        'all',
        'active',
        'completed'
      ]
    }),
    computed:{
      itemsLength(todo){
        return this.todos.filter(todo =>!todo.completed).length
        // return this.todos.filter(function(todo){
        //   return !todo.completed
        // }).length
      }
    },
    methods:{
      toggle(tab){
        this.$emit('toggle',tab)
      },
      clearCompleted(){
        this.$emit('clear')
      }
    }
  }
</script>

<style scoped>
  .footer{
    margin: 0 40px;
    display: flex;
    justify-content: space-between;
    background:rgba(0,0,0,.5);
    border-radius: 20px;
    line-height: 50px;
    padding: 0 20px;
  }
  .footer span{
    color:#fff;
    font-size: 20px;
    cursor: pointer;
  }
  .tab_content{
    display: flex;
  }
  .tab_content span{
    display: block;
    flex-grow: 1;
    margin: 0 10px;
    padding: 0 5px;
  }
  .tab_content .actived{
    background: #dc3545;
    border-radius: 0 35px 10px 0;
  }
</style>
