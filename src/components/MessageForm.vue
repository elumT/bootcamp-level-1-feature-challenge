<script setup>
import { faker } from "@faker-js/faker";
import {ref} from "vue"

const userMessage = ref('')

const emits = defineEmits(['send-msg'])

function sendMessage() {
  const newMessage = {
    id: Math.floor(Math.random()).toLocaleString(),
    author: faker.person.firstName(),
    content: userMessage.value,
    timestamp: new Date().toLocaleString(),
  }
  emits('send-msg', newMessage)
  userMessage.value = ''
}
</script>

<template>
  <form class="mt-2" @submit.prevent="sendMessage">
    <input type="text" class="input-box" v-model="userMessage">
    <button type="submit" class="send-btn" :disabled="userMessage.length === 0">Submit</button>
  </form>
</template>
