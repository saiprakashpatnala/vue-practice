<script setup>
import {ref} from "vue"
import TasksList from './TasksList.vue'

let task=ref("")
let data=ref([])

const add=()=>{
    if(task.value.trim().length!==0){
        data.value.push(task.value)
    }
    task.value=""
}

let removeTask=(id)=>{
    data.value.splice(id,1)
}
</script>

<template>
    <h1>TodoList</h1>
    <form @submit.prevent="add">
        <input type="text" v-model="task"/>
        <button type="submit">Add Task</button>
    </form>
    <ul>
    <TasksList :data="data" :removeTask="removeTask"/>
    </ul>

</template>

<style scoped>
.number {
    color: red;
}
</style>
