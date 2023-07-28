<template>
  <header
    class="flex justify-between items-center p-5 bg-gray-600 text-gray-200 sticky top-0 z-10"
  >
    <nuxt-link to="/"><img src="/favicon.ico" alt="" /></nuxt-link>

    <nuxt-link
      to="/employee/create"
      class="border p-2 rounded-md hover:bg-gray-200 hover:text-gray-600"
      >Create a new employee</nuxt-link
    >
  </header>
</template>
