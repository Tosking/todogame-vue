<template>
        <form @submit.prevent>
            <input type="text" v-model="task.title" class="input" placeholder="Title"/>
            <input type="text" v-model="task.body" class="input" placeholder="Body"/>
            <button class="button" @click="addTask">
                Add Task
            </button>
        </form>
</template>

<script>
export default {
    data() {
        return{
            task: {
                title: '',
                body: ''
            }
        }
    },
    methods: {
        addTask(){
            if(this.isEmptyOrSpaces(this.task.title)){
                return;
            }
            this.tasks += 1;
            this.$emit('add', this.task);
            this.task = {
                title: '',
                body: ''
            }
        },
        isEmptyOrSpaces(str){
            return str === null || str.match(/^ *$/) !== null;
        }
    }
}
</script>

<style>
    .input {
        margin-top: 10px;
        width: 100%;
    }
    .button {
        margin-top: 10px;
        width: 100%;
    }
</style>