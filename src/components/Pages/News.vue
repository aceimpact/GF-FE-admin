<template>
  <div>
    <CommonHeader title="ニュース一覧"></CommonHeader>

    <div class="flex justify-end items-center">
      <BaseButton color="primary" prepend-icon="add"> 新規登録 </BaseButton>
    </div>

    <UniquesNewsDataTable
      class="mt-4"
      :data="displayData"
    ></UniquesNewsDataTable>

    <CommonPagination
      class="mt-10"
      :pagination="pagination"
      @click:first="pagination.page = $event"
      @click:last="pagination.page = $event"
      @click:next="pagination.page = $event"
      @click:prev="pagination.page = $event"
    ></CommonPagination>
  </div>
</template>

<script lang="ts" setup>
import { ref, computed, onMounted } from 'vue';

const originalData = ref([]);
const pagination = ref({
  lastPage: 0,
  page: 1,
  perPage: 10,
} as {
  lastPage: number;
  page: number;
  perPage: number;
});

const fetchData = async () => {
  const { data: NewsRepositories } = await useFetch(
    'http://127.0.0.1:8000/api/news',
  );

  originalData.value = NewsRepositories.value;

  pagination.value.lastPage = Math.ceil(
    NewsRepositories.value.length / pagination.value.perPage,
  );
};

const displayData = computed(() => {
  const start: number = (pagination.value.page - 1) * pagination.value.perPage;
  const end: number = start + pagination.value.perPage;

  return originalData.value.slice(start, end);
});

onMounted(fetchData);
</script>
