<script setup>
import {ref} from "vue"
let quote=ref({})
let data=ref([
    {
        "quote": "The only way to do great work is to love what you do.",
        "author": "Steve Jobs"
    },
    {
        "quote": "In three words I can sum up everything I've learned about life: it goes on.",
        "author": "Robert Frost"
    },
    {
        "quote": "The future belongs to those who believe in the beauty of their dreams.",
        "author": "Eleanor Roosevelt"
    },
    {
        "quote": "Don't watch the clock; do what it does. Keep going.",
        "author": "Sam Levenson"
    },
    {
        "quote": "Success is not final, failure is not fatal: It is the courage to continue that counts.",
        "author": "Winston Churchill"
    },
    {
        "quote": "Life is what happens when you're busy making other plans.",
        "author": "John Lennon"
    },
    {
        "quote": "The only limit to our realization of tomorrow will be our doubts of today.",
        "author": "Franklin D. Roosevelt"
    },
    {
        "quote": "Believe you can and you're halfway there.",
        "author": "Theodore Roosevelt"
    },
    {
        "quote": "Be yourself; everyone else is already taken.",
        "author": "Oscar Wilde"
    },
    {
        "quote": "Happiness is not by chance, but by choice.",
        "author": "Jim Rohn"
    }
]
)
console.log(data.value.length)

const getRandomQuote=()=>{
    let val=Math.ceil(Math.random()*data.value.length-1)
    console.log(val)
    quote.value=data.value[val]

}
</script>

<template>
    <h1>Random Quote</h1>
    <button @click="getRandomQuote">Click</button>
    <div>
     <h1>{{ quote.quote }}</h1>
     <p>{{ quote.author }}</p>
    </div>
</template>