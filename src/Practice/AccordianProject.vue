<script setup>
import { ref, computed } from "vue";
let isLoading=ref(false)
const planetsData = [
    {
        name: "Mercury",
        diameter: 4879,
        distanceFromSun: 57.91,
        moons: 0,
    },
    {
        name: "Venus",
        diameter: 12104,
        distanceFromSun: 108.2,
        moons: 0,
    },
    {
        name: "Earth",
        diameter: 12742,
        distanceFromSun: 149.6,
        moons: 1,
    },
    {
        name: "Mars",
        diameter: 6779,
        distanceFromSun: 227.9,
        moons: 2,
    },
    {
        name: "Jupiter",
        diameter: 139820,
        distanceFromSun: 778.3,
        moons: 79,
    },
    {
        name: "Saturn",
        diameter: 116460,
        distanceFromSun: 1427,
        moons: 83,
    },
    {
        name: "Uranus",
        diameter: 50724,
        distanceFromSun: 2871,
        moons: 27,
    },
    {
        name: "Neptune",
        diameter: 49244,
        distanceFromSun: 4497,
        moons: 14,
    },
    {
        name: "Pluto",
        diameter: 2370,
        distanceFromSun: 5913,
        moons: 5,
    },
];

let val = ref(0);

let increment = () => {
    isLoading.value=true
    if (val.value >= 0 && val.value < planetsData.length - 1) {
        val.value += 1;
       
    }
     isLoading.value=false
};

let decrement = () => {
    isLoading.value=true
    if (val.value > 0) {
        val.value -= 1;
        
    }
    isLoading.value=false

};

let getPlanet = computed(() => {
    return planetsData[val.value];
});
</script>

<template>
    <h1>Planets</h1>
    <button @click="increment">▶️</button>
    <p v-if="isLoading">Loading.....</p>
    <div v-else>
    <p>{{ getPlanet.name }}</p>
    <p>{{ getPlanet.diameter }}</p>
    <p>{{ getPlanet.distanceFromSun }}</p>
    <p>{{ getPlanet.moons }}</p>
    </div>
    <button @click="decrement">◀️</button>
</template>
