<template>
  <div class="p-6">
    <div class="flex">
      <input
        v-model="newMessage"
        class="py-1 px-2 rounded border-2"
        type="text"
      />
      <button
        class="ml-1 py-1 px-2 bg-gray-200 rounded border-2"
        @click="onClickAddButton"
      >
        add
      </button>
    </div>
    <div class="mt-4">
      <p
        v-for="(message, index) in messageList"
        :key="index"
        class="mt-1 text-gray-400"
      >
        {{ message.text }}
      </p>
      <p v-if="!messageList.length" class="mt-1 text-gray-400">no messages</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const newMessage = ref<string>('')
const messageList = ref<{ text: string }[]>([])

function onClickAddButton(): void {
  messageList.value.push({ text: newMessage.value } as { text: string })
  newMessage.value = ''
}
</script>
