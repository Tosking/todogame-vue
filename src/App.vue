<template>
    <div class="app">
        <div>
            Кол-во задач {{ tasks }}
        </div>
        <task-list
        :taskArr="taskArr"
        />
        <add-task-form
        @add="addTask"
        />
        <APIrequest
        @getTask="getTask"
        />
    </div>
</template>

<script>
import TaskList from "@/components/TaskList.vue"
import AddTaskForm from "@/components/AddTaskForm.vue"
import APIrequest from "@/components/APIrequest.vue"
export default {
    components: {
        TaskList, AddTaskForm,
        APIrequest
    },
    data(){
        return{
            tasks: 0,
            taskArr: [],
        }
    },
    methods: {
        addTask(task){
            this.taskArr.push(task);
        },
        getTask(response){
            for(var i = 0; i < response.data.length; i++){
                this.taskArr.push({
                    title: response.data[i][4],
                    body: response.data[i][3]
                })
                console.log(response.data[i]);
            }
        }
    }
}
</script>

<style>

    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }
    .app {
        padding: 50px;
    }
</style>