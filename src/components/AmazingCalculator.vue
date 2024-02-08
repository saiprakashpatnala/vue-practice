<script setup>
import { ref } from "vue";
const value = ref("");

const getCalculation=(val)=>{
    if(val==="C"){
        value.value=""
    }
    else if(val==="="){
        let num=eval(value.value).toString()
        value.value=num
    }
    else{
        value.value+=val
    }
}
</script>

<template>
  <input type="text" v-model="value" />
  <button @click="getCalculation('+')">+</button>
  <button @click="getCalculation('-')">-</button>
  <button @click="getCalculation('*')">*</button>
  <button @click="getCalculation('/')">/</button>
  <button @click="getCalculation('%')">%</button>
  <button @click="getCalculation('=')">=</button>
  <button @click="getCalculation('C')">C</button>
  <button @click="getCalculation('1')">1</button>
  <button @click="getCalculation('2')">2</button>
  <button @click="getCalculation('3')">3</button>
  <button @click="getCalculation('4')">4</button>
  <button @click="getCalculation('5')">5</button>
  <button @click="getCalculation('6')">6</button>
  <button @click="getCalculation('7')">7</button>
  <button @click="getCalculation('8')">8</button>
  <button @click="getCalculation('9')">9</button>
  <button @click="getCalculation('0')">0</button>
</template>
