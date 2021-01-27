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
                <input type="checkbox" class="mr-2" @click="check(index)" :id="index">
                {{item.value}}
            </td>
            <td>{{item.date}}</td>
            <td>{{item.time}}</td>
            <td><span class="fa fa-trash text-danger"></span></td>
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
            tasksArray:this.task
        }
    },
    methods:{
        check:function(val){
            var checkBox = document.getElementById(val)
            if(checkBox.checked){
                this.tasksArray[val].status="checked"
                this.checked+=1
            }else{
                this.tasksArray[val].status="unchecked"
                this.checked-=1

            }
            this.$emit("checkedTask",this.tasksArray,this.checked)
        }
    }
}
</script>
<style scoped>
    .strike{
        text-decoration: line-through;
        /* background-color: #d7dde2; */
    }
</style>