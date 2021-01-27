<template lang="">
    <div class="row card">
    <table class="table table-hover text-left" id="tab">
        <thead class="thead-dark">
            <tr>
            <th scope="col">Task</th>
            <th scope="col">Date Due</th>
            <th scope="col">Time Due</th>
            <th scope="col"><div class="fa fa-trash"></div></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(item,index) in tasksArray" :key="index" :class="item.status=='checked'?'strike':''">
            <td scope="row">
                <input type="checkbox" class="mr-2" @click="check(index)" :id="index" :checked="item.status=='checked'?true:false">
                {{item.value}}
            </td>
            <td>{{item.date}}</td>
            <td>{{item.time}}</td>
            <td><span class="fa fa-trash text-danger pointDel" @click="deleteItem(index)"></span></td>
            </tr>
        </tbody>
    </table>
    </div>
</template>
<script>
export default {
    name:'Items',
    props:{
        task:Array,
        checked:Number
    },
    data(){
        return{
            tasksArray:this.task,
            checkedValue:this.checked
        }
    },
    methods:{
        check:function(val){
            var checkBox = document.getElementById(val)
            if(checkBox.checked){
                this.tasksArray[val].status="checked"
                this.checkedValue+=1
            }else{
                this.tasksArray[val].status="unchecked"
                this.checkedValue-=1

            }
            this.$emit("checkedTask",this.tasksArray,this.checkedValue)
        },
        deleteItem:function(index){
            // alert(index)
            if(this.tasksArray[index].status=="checked"){
                this.checkedValue-=1
            }
            this.tasksArray.splice(index,1)
            console.log(this.tasksArray)
            this.$emit("deletedTask",this.tasksArray,this.checkedValue)
        }
    }
}
</script>
<style scoped>
    .strike{
        text-decoration: line-through;
        /* background-color: #d7dde2; */
    }
    .pointDel{
        cursor: pointer;
    }
</style>