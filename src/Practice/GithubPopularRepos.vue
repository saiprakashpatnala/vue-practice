<script setup>
import { ref } from "vue";

let repo = ref("ALL");
let data = ref([]);
let isLoading = ref(false);
const languageFiltersData = [
    { id: "ALL", language: "All" },
    { id: "JAVASCRIPT", language: "Javascript" },
    { id: "RUBY", language: "Ruby" },
    { id: "JAVA", language: "Java" },
    { id: "CSS", language: "CSS" },
];

let getData = async (val) => {
    isLoading.value = true;
    try {
        let respnse = await fetch(
            `https://apis.ccbp.in/popular-repos?language=${val}`
        );
        if (respnse.ok) {
            let fdata = await respnse.json();
            console.log(fdata);
            data.value = fdata.popular_repos;
        }
    } catch (e) {
        console.log(e);
    } finally {
        isLoading.value = false;
    }
};
let getFilterRepo = (i) => {
    repo.value = i;
    getData(i);
};

let getClass = (i) => {
    return {
        active: i === repo.value,
        notactive: i !== repo.value,
    };
};
getData(repo.value);
</script>

<template>
    <div>
        <div v-if="isLoading" class="text-center">

            <b-spinner label="Spinning">llll</b-spinner>
            <b-spinner type="grow" label="Spinning"></b-spinner>


        </div>

        <div v-else>
            <h1 class="header">GitHub Popular Repos</h1>

            <div class="filters-container">
                <button v-for="item in languageFiltersData" :key="item.id" :class="getClass(item.id)"
                    @click="getFilterRepo(item.id)">
                    {{ item.language }}
                </button>
            </div>

            <ul class="repos-list">
                <li v-for="item in data" :key="item.id" class="repo-item">
                    <img :src="item.avatar_url" :alt="item.name" class="repo-avatar" />
                    <div class="repo-details">
                        <p class="repo-name">{{ item.name }}</p>
                        <div class="repo-stats">
                            <span class="repo-forks">Forks: {{ item.forks_count }}</span>
                            <span class="repo-issues">Issues: {{ item.issues_count }}</span>
                            <span class="repo-stars">Stars: {{ item.stars }}</span>
                        </div>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
.header {
    text-align: center;
    font-size: 24px;
    margin-bottom: 20px;
}

.filters-container {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-bottom: 20px;
    list-style-type: none;
}

.repos-list {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    padding-left: 0px;
}

.repo-item {
    list-style-type: none;
    width: 20%;
}

.repo-avatar {
    height: 120px;
    width: 150px;
}

button {
    cursor: pointer;
    padding: 10px;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    transition: background-color 0.3s;
}

.active {
    color: #0284c7;
    background-color: #ffffff;
    border: 1px solid #0284c7;
}
</style>



