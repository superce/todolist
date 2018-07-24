<template>
  <div class="footer">
    <div class="tab_left">
      <span>
        item
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
      <span @click="clear()">
        clear
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
      }
    },
    data:() => ({
      tabs:[
        'all',
        'active',
        'completed'
      ]
    }),
    methods:{
      clear(){

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
  .tab_content span{
    margin: 0 10px;
  }
  .tab_content .actived{
    border: 1px solid #fff;
  }
</style>
