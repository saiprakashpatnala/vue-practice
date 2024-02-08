<script setup>
import {ref} from "vue"
let data=ref([])
let isLoading=ref(false)

let getData=async()=>{
    try{
        isLoading.value=true
        let respnse=await fetch("https://apis.ccbp.in/tg/packages")
        if(respnse.ok){
            let fdata=await respnse.json()
            data.value=fdata.packages
            console.log(data.value)
        }

    }
    catch(e){
        console.log(console.error)
    }
    finally{
     isLoading.value=false
    }
}

getData()
</script>

<template>
    <h1>Tourist Guide</h1>
    <p v-if="isLoading">Loading......</p>
    <ul>
        <li v-for="(item) in data" :key="item.id">
         <img :src="item.image_url" :alt="item.name"/>
         <p>{{ item.name }}</p>
         <p>{{ item.description }}</p>

        </li>
    </ul>
</template>