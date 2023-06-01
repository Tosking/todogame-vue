<template>
    <div>
        <div>
            Кол-во задач {{ tasks }}
        </div>
        <button @click="addTask">
            Add Task
        </button>
    </div>
</template>

<script>
export default {
    
    data(){
        return{
            tasks: 0
        }
    },
    methods: {
        addTask(){
            this.tasks += 1;
        }
    }
}
</script>

<style lang="sass">
    *
        padding: 0
        margin: 0
        box-sizing: border-box
    .task
        padding: 15px
        border: 2px solid
        margin-top: 10px
        border-radius: 10px
</style>