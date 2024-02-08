<script setup>
import {ref} from "vue"
const toggle=ref(true)
let val=ref("")

const toggleText=()=>{
    toggle.value=!toggle.value
}
</script>

<template>
    <div v-if="toggle">
        <input type="text" v-model="val"/>
        <button @click="toggleText">Save</button>
    </div>
    <div v-else>
        <p>{{ val }}</p>
        <button @click="toggleText">Edit</button>
    </div>
</template>