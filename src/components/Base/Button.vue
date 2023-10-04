<template>
  <button
    class="flex justify-start items-center py-2 px-4 rounded-lg duration-300 hover:bg-gray-100"
    :class="{ 'bg-cyan-500 text-white': color === 'primary' }"
    @click="onClick"
  >
    <span v-if="prependIcon" class="mdi mdi-plus mr-2"></span>
    <slot></slot>
    <span v-if="appendIcon" class="mdi mdi-logout ml-2"></span>
  </button>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  color: String,
  prependIcon: String,
  appendIcon: String,
})

const color = ref(props.color)
const prependIcon = ref(props.prependIcon)
const appendIcon = ref(props.appendIcon)

function onClick() {}
</script>
