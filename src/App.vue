<template>
  <div>
    <nav class="navbar navbar-light bg-dark p-3">
      <span class="navbar-brand mb-0 h1 d-block mx-auto text-white">My Todo</span>
    </nav>
    <div id="app" class="col-md-7 mx-auto">
    {{checked +"/"+ task.length}}
    <Input @add-task="newTask"/>
    <Items :task="task" :checked="checked" @checkedTask="checkTasks"/>
  </div>
  </div>
</template>

<script>
import Input from './components/input'
import Items from './components/items'
export default {
  name: 'App',
  components: {
    Input,
    Items
  },
  data(){
    return{
      task:[],
      checked:0
    }
  },
  methods:{
    newTask:function(value,date,time){
      // alert(value)
      this.task.push({value,date,time,status:"unchecked"})
    },
    checkTasks(value,check){
      console.log(value);
      this.task=value
      this.checked=check
    }
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
