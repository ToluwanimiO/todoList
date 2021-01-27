<template lang="">
    <div class="row p-0 mb-3" id="con">
        <div class="col-5 p-0">
            <input type="text" class="form-control rounded-0" id="inp" placeholder="Enter task" v-model="task"/>
        </div>
        <div class="col-3 p-0">
            <input type="date" class="form-control rounded-0" id="inp" placeholder="Deadline" v-model="date"/>
        </div>
        <div class="col-3 p-0">
            <input type="time" class="form-control rounded-0" id="inp" placeholder="Deadline" v-model="time"/>
        </div>
        <div class="col-1 bg-dark" id="addBg" @click="addTask">
            <span class="fa fa-plus text-white"></span>
        </div>
    </div>
</template>
<script>
export default {
    name:"Input",
    data(){
        return{
            task:"",
            date:"",
            time:""
        }
    },
    methods:{
        addTask:function(){
            // let currentDate = new Date().toLocaleDateString("fr-CA")
            // let currentTime = new Date().toLocaleTimeString().slice(0,5)
            this.$emit("add-task",this.task,this.date,this.time)
            this.task=""
            this.date=""
            this.time=""
        }
    }
}
</script>
<style scoped>
    #addBg{
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
    }
    #inp:focus{
        box-shadow:none;
        border-color:#CED4DA;
    }
    #con:hover{
        color: #495057;
        border-color: #d2e3f7;
        outline: 0;
        box-shadow: 0 0 0 0.1rem rgba(218, 227, 236, 0.25);
    }
</style>