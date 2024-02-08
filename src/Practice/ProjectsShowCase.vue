<script setup>
import { ref } from "vue"
const data = ref([])
const name = ref("ALL")
let isLoading=ref(false)
const categoriesList = [
    { id: 'ALL', displayText: 'All' },
    { id: 'STATIC', displayText: 'Static' },
    { id: 'RESPONSIVE', displayText: 'Responsive' },
    { id: 'DYNAMIC', displayText: 'Dynamic' },
    { id: 'REACT', displayText: 'React' },
]

let getData = async (val) => {
    isLoading.value=true
    try {
        let response = await fetch(`https://apis.ccbp.in/ps/projects?category=${val}`)
        if (response.ok) {
            let fdata = await response.json()
            data.value = fdata.projects
        }
    }
    catch (e) {
        console.log(e)
    }

    finally{
        isLoading.value=false
    }
}


let changeCategory = (e) => {
    name.value = (e.target.value)
    getData(e.target.value)
}
getData(name.value)
</script>

<template>
    <h1>Project Showcase</h1>
    <select v-model="name" @change="changeCategory">
        <option v-for="(item) in categoriesList" :key="item.id" :value="item.id">{{ item.displayText }}</option>
    </select>
    <p v-if="isLoading">Loading...</p>

    <ul v-else>
        <li v-for="(item) in data" :key="item.id">
            <img :src="item.image_url" :alt="item.name" />
            <p>{{ item.name }}</p>
        </li>
    </ul>
</template>