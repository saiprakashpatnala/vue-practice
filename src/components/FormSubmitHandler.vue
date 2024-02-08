<script setup>
import { ref, computed } from "vue"
let name = ref("")
let email = ref("")
let password = ref("")
let validName = computed(() => name.value.trim().length > 0)
let validEmail = computed(() => email.value.endsWith("@email.com"))
let validPassword = computed(() => password.value.length > 8)
let validCreds = computed(() => validName.value && validEmail.value && validPassword.value)

const formHandler = () => {
    if (validCreds.value) {
        console.log("Login Sucessfully")
    }
    else {
        console.log("Failed to Login")
    }
    name.value=""
    email.value=""
    password.value=""
}
</script>

<template>
    <form @submit.prevent="formHandler">
        <input type="name" v-model="name" />
        <input type="email" v-model="email" />
        <input type="password" v-model="password" />
        <button type="submit">Submit</button>
    </form>
</template>