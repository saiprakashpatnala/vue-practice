<script setup>
import {ref} from "vue"
let text=ref("")
let arr=ref([])

let addCharacter=()=>{
    if(text.value.trim().length>0){
        arr.value.push(text.value)
    }
    text.value=""
}
</script>

<template>
    <h1>Count Characters</h1>
    <form @submit.prevent="addCharacter">
    <input type="text" v-model="text"/>
    <button type="submit">Add</button>
    </form>
    <ul>
        <li v-for="(item,index) in arr" :key="index">
          <p>{{ item }}</p>
         <span>{{ item.length }}</span>
        </li>
    </ul>
</template>