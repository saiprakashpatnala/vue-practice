<script setup>
import {ref} from "vue"
const data=ref([])
let obj=ref({})

const getJoke=async()=>{
   try{
    let response=await fetch("https://apis.ccbp.in/jokes/random")
    let arr=await response.json()
    data.value=arr
    obj.value=data.value
   }

   catch(e){
    console.log(e)
   }
}
</script>
<template>
    <h1>Click Button to get Random Joke</h1>
    <button @click="getJoke">Click</button>
    <h1>{{ obj.value }}</h1>
</template>