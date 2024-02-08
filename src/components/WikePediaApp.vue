<script setup>
import { ref } from "vue";
let query = ref("");
const data = ref([]);

const getDetails = async (e) => {
    if (e.key === "Enter") {
        let response = await fetch(
            `https://apis.ccbp.in/wiki-search?search=${query.value}`
        );
        let fdata = await response.json();
        data.value = fdata.search_results;
    }
};
</script>

<template>
    <h1>Wikepedia Application</h1>
    <input type="search" v-model="query" @keyup="getDetails" />
    <ul>
        <li v-for="item in data">
            <a :href="item.link" target="_blank">{{ item.title }}</a>
            <h1>{{ item.title }}</h1>
            <p>{{ item.description }}</p>
        </li>
    </ul>
</template>
