<template>
  <div class="flex">
    <div
      class="h-screen text-white"
      style="background-color: #546e7a; width: 400px"
    >
      <span class="block text-2xl ml-4 mt-10 font-bold">
        Growfit Headless CMS
      </span>

      <div class="flex items-center mt-10 ml-4">
        <span class="block text-xs whitespace-nowrap">コンテンツ</span>
        <div class="h-0 w-full ml-2 border-t border-dashed"></div>
      </div>

      <NuxtLink
        class="flex items-center w-full mt-5 p-4 rounded-lg duration-300 hover:opacity-80"
        :class="{ 'bg-cyan-500': $route.name === 'news' }"
        to="/news"
      >
        <span class="mdi mdi-text-box-outline pr-4"></span>
        <span class="block ml-4">ニュース</span>
      </NuxtLink>
    </div>
    <main>
      <slot />
    </main>
  </div>
</template>
