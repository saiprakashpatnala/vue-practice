<script setup>
import {ref} from "vue"
const name=ref("")
const data=ref([])

const submitHandler=()=>{
    if(name.value.trim().length!==0){
        data.value.push(name.value)
    }
    name.value=""
}

const deleteTodo=(id)=>{
    data.value.splice(id,1)
}
</script>

<template>
    <h1>Todo List</h1>
    <form @submit.prevent="submitHandler">
    <input type="text" v-model="name"/>
    <button type="submit">Add</button>
    </form>
    <ul>
        <li v-for="(item,index) in data" :key="index">
           <p>{{ item}}</p>
           <button @click="deleteTodo">Delete</button>
        </li>
    </ul>
</template>