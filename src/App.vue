<template>
  <div>
    <div class="col-md-9 mx-auto pt-5">
      <p class="text-center">{{checked+"/"+task.length}}</p>
      <Input @add-task="newTask"/>
      <Items :task="task" :checked="checked" @checkedTask="checkTask" @deletedTask="deleteTask"/>
    </div>
  </div>  
</template>

<script>
import Input from './components/input';
import Items from './components/items';
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
      console.log(value)
      this.task.push({value,date,time,status:"unchecked"})
    },
    checkTask:function(value,checkVal){
      this.task=value;
      this.checked=checkVal;
    },
    deleteTask:function(value,checkVal){
      this.task=value;
      this.checked=checkVal;

    }
  }
  
}
</script>

<style scoped>

</style>
