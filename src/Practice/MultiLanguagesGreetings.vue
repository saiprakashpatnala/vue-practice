<script setup>
import { ref,computed } from "vue";

let languageGreetingsList = [
  {
    id: 'bfdf40eb-eec9-4a66-a493-752fe689f0d0',
    imageUrl: 'https://assets.ccbp.in/frontend/react-js/multilingual_greeting/english-greetings-img.png',
    buttonText: 'English',
    imageAltText: 'english',
  },
  {
    id: '0ceda891-2a0c-49e2-8c62-68e78180bac6',
    imageUrl: 'https://assets.ccbp.in/frontend/react-js/multilingual_greeting/tamil-greetings-img.png',
    buttonText: 'Tamil',
    imageAltText: 'tamil',
  },
  {
    id: '89537778-7a46-4c58-988c-0adc931d087c',
    imageUrl: 'https://assets.ccbp.in/frontend/react-js/multilingual_greeting/telugu-greetings-img.png',
    buttonText: 'Telugu',
    imageAltText: 'telugu',
  }
];

let index = ref(0);


let setImages=computed(()=>{
    return languageGreetingsList[index.value]
})

let setIndex = (k) => {
  index.value = k;
  
};
</script>

<template>
  <div>
    <h1>MultiLingual Greetings</h1>
    <button @click="setIndex(0)">English</button>
    <button @click="setIndex(1)">Tamil</button>
    <button @click="setIndex(2)">Telugu</button>
    <div>
      <img :src="setImages.imageUrl" :alt="setImages.imageAltText" />
      <p>{{ imageAltText }}</p>
    </div>
  </div>
</template>
