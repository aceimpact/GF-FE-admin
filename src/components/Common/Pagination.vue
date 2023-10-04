<template>
  <div class="flex justify-center items-center">
    <button @click="onClickFirst">
      <span
        class="mdi mdi-chevron-double-left flex text-cyan-500 duration-300 hover:opacity-80"
      ></span>
    </button>
    <button>
      <span
        class="mdi mdi-chevron-left flex text-cyan-500 duration-300 hover:opacity-80"
        @click="onClickPrev"
      >
      </span>
    </button>
    <button
      v-if="pagination.page - 1 > 0"
      class="flex justify-center items-center h-30px w-30px ml-4 border rounded-lg text-sm duration-300 hover:bg-gray-100"
      @click="onClickPrev"
    >
      {{ pagination.page - 1 }}
    </button>
    <button
      class="flex justify-center items-center h-30px w-30px ml-4 bg-primary rounded-lg text-sm text-white duration-300 hover:opacity-80"
    >
      {{ pagination.page }}
    </button>
    <button
      v-if="pagination.page + 1 <= pagination.lastPage"
      class="flex justify-center items-center h-30px w-30px ml-4 border rounded-lg text-sm duration-300 hover:bg-gray-100"
      @click="onClickNext"
    >
      {{ pagination.page + 1 }}
    </button>
    <button @click="onClickNext">
      <span
        class="mdi mdi-chevron-right flex ml-4 text-cyan-500 duration-300 hover:opacity-80"
      >
      </span>
    </button>
    <button @click="onClickLast">
      <span
        class="mdi mdi-chevron-double-right flex text-cyan-500 duration-300 hover:opacity-80"
      >
      </span>
    </button>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import { Common } from '@/types';

const props = defineProps({
  pagination: {
    type: Object as () => Common.Pagination,
    required: false,
    default: () => ({}),
  },
});

const pagination = ref(props.pagination);

const emit = defineEmits<{ (e: 'click', first?: number): void }>();

const onClickFirst = (): number => {
  return 1;
};

const onClickLast = (): number => {
  return props.pagination.lastPage;
};

const onClickNext = (): number => {
  return props.pagination.page < props.pagination.lastPage
    ? props.pagination.page + 1
    : props.pagination.page;
};

const onClickPrev = (): number => {
  return props.pagination.page > 1
    ? props.pagination.page - 1
    : props.pagination.page;
};
</script>
