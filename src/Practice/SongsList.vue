<script setup>
 defineProps(["data","removeSong"])
 
</script>

<template>
    <li v-for="(item,index) in data" :key="index">
    <img :src="item.imageUrl" alt="item.name"/>
    <p>{{ item.name }}</p>
    <p>{{ item.genre }}</p>
    <p>{{ item.duration }}</p>
    <button @click="removeSong(index)">Delete</button>
    </li>
</template>