<template>
  <div class="flex justify-between items-center pl-6 pr-4 h-104px">
    <span class="text-xl">{{ title }}</span>
    <BaseButton append-icon="logout" @click="onClickLogout">
      ログアウト
    </BaseButton>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const props = defineProps({
  title: {
    type: String,
    required: false,
    default: '',
  },
});

// TODO
const emit = defineEmits<{ (e: 'click', logout?: string): void }>();

const title = ref(props.title);

const onClickLogout = () => {
  emit('click');
};
</script>
