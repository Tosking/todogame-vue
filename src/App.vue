<template>
    <div class="app">
        <div>
            Кол-во задач {{ tasks }}
        </div>
        <div v-if="authorized">
            <div class="auth">
                You successfully authorized! Your id is <strong>{{ id }}</strong>
            </div>
        </div>
        <login-modal :show="showLoginModal">
            <login-form
            @login="login"
            />
        </login-modal>
        <task-list
        :taskArr="taskArr"
        />
        <add-task-form
        @add="addTask"
        />
    </div>
</template>

<script>
import TaskList from "@/components/TaskList.vue"
import AddTaskForm from "@/components/AddTaskForm.vue"
import LoginModal from '@/components/LoginModal.vue'
import LoginForm from "./components/LoginForm.vue"
import axios from "axios";
export default {
    components: {
        TaskList, AddTaskForm,
        LoginModal, LoginForm
    },
    data(){
        return{
            tasks: 0,
            taskArr: [],
            id: 0,
            authorized: false,
            showLoginModal: true
        }
    },
    methods: {
        addTask(task){
            this.taskArr.push(task);
        },
        login(id){
            this.authorized = true;
            this.showLoginModal = false;
            this.id = id;
            axios.post("http://127.0.0.1:5000/get/task", {id: this.id, list: 23})
            .then(response => {
                console.log(response.data); 
                for(var i = 0; i < response.data.length; i++){ 
                    this.addTask({title: response.data[i][1], body: response.data[i][4]});
                    this.tasks++;
                }
            }).catch(error => console.log(error));
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