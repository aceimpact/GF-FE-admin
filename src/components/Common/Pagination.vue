<template>
  <div class="flex justify-center items-center">
    <button @click="toFirstPage">
      <span
        class="mdi mdi-chevron-double-left flex text-cyan-500 duration-300 hover:opacity-80"
      ></span>
    </button>
    <button>
      <span
        class="mdi mdi-chevron-left flex text-cyan-500 duration-300 hover:opacity-80"
        @click="toPrevPage"
      >
      </span>
    </button>
    <button
      v-if="pagination.page - 1 > 0"
      class="flex justify-center items-center h-7 w-7 ml-4 border rounded-lg text-sm duration-300 hover:bg-gray-100"
      @click="toPrevPage"
    >
      {{ pagination.page - 1 }}
    </button>
    <button
      class="flex justify-center items-center h-7 w-7 ml-4 bg-cyan-500 rounded-lg text-sm text-white duration-300 hover:opacity-80"
    >
      {{ pagination.page }}
    </button>
    <button
      v-if="pagination.page + 1 <= pagination.lastPage"
      class="flex justify-center items-center h-7 w-7 ml-4 border rounded-lg text-sm duration-300 hover:bg-gray-100"
      @click="toNextPage"
    >
      {{ pagination.page + 1 }}
    </button>
    <button @click="toNextPage">
      <span
        class="mdi mdi-chevron-right flex ml-4 text-cyan-500 duration-300 hover:opacity-80"
      >
      </span>
    </button>
    <button @click="toLastPage">
      <span
        class="mdi mdi-chevron-double-right flex text-cyan-500 duration-300 hover:opacity-80"
      >
      </span>
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { Common } from '@/types';

const props = defineProps({
  pagination: {
    type: Object as () => Common.Pagination,
    required: false,
    default: () => ({}) as Common.Pagination,
  },
});

const pagination = ref(props.pagination);

// const { emit } = defineEmits([
//   'click:first',
//   'click:last',
//   'click:next',
//   'click:prev',
// ]);

const toFirstPage = () => {
  this.$emit('click:first', 1);
};
// function toFirstPage() {
//   pagination.value.page = 1;
// }

const toNextPage = () => {
  const nextPage =
    props.pagination.page < props.pagination.lastPage
      ? props.pagination.page + 1
      : props.pagination.page;
  emit('click:next', nextPage);
};
// function toNextPage() {
//   if (pagination.value.page < pagination.value.lastPage) {
//     pagination.value.page++;
//   }
// }

function toLastPage() {
  pagination.value.page = pagination.value.lastPage;
}

function toPrevPage() {
  if (pagination.value.page > 1) {
    pagination.value.page--;
  }
}

// const onClickFirst = (): number => {
//   return 1;
// };

// const onClickLast = (): number => {
//   return props.pagination.lastPage;
// };

// const onClickNext = (): number => {
//   return props.pagination.page < props.pagination.lastPage
//     ? props.pagination.page + 1
//     : props.pagination.page;
// };

// const onClickPrev = (): number => {
//   return props.pagination.page > 1
//     ? props.pagination.page - 1
//     : props.pagination.page;
// };
</script>
