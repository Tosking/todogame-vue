<template>
    <div class="task" v-for="(task, i) in taskArr" v-bind:key="i">
        {{ task.title }}
        <div class="task-body">
            {{ task.body }}
        </div>
    </div>
</template>

<script>
export default {
    props: {
        taskArr: {
            type: Array,
            required: true
        }
    }

}
</script>

<style scoped>
    .task {
        font-size: 30px;
        border: 2px solid;
        padding: 10px;
        border-radius: 10px;
        margin-top: 10px;
        color: white;
        background-color: rgb(0, 60, 255);
    }
    .task-body {
        font-size: 15px;
    }
</style>