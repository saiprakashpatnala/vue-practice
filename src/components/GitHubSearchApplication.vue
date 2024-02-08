<script setup>
import {ref} from "vue"
let query=ref("")
let data=ref([])
let userObject=ref({})

let searchUser=async(e)=>{
    if(e.key==="Enter"){
     let response=await fetch(`https://api.github.com/users/${query.value}`)
     let fdata=await response.json()
     data.value=fdata
     userObject.value=data.value
     console.log(data.value)
    }

}
</script>

<template>
    <h1>git-hub</h1>
    <input type="search" v-model="query" @keyup="searchUser"/>
    <div v-if="userObject.length!==0">
    <h1>{{ userObject.login }}</h1>
    <img :src="userObject.avatar_url" alt="userObject.login"/>
    </div>
</template>