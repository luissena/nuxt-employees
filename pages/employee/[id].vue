<script setup lang="ts">
import { Employee } from "../../types/employee.type";
const $route = useRoute();

const { data: employee } = await useFetch<Employee>(
  `http://localhost:3000/employees/${$route.params.id}`
);
</script>

<template>
  <Title>Employee: {{ employee?.first_name || "Not found" }}</Title>
  <section class="max-w-7xl mx-auto" v-if="employee">
    <div
      class="flex flex-col md:flex-row justify-center items-center gap-10 border shadow-sm rounded-es-md rounded-ee-md md:w-2/3 mx-auto p-5"
    >
      <img
        v-if="employee.avatar"
        class="rounded-full border w-36 h-36"
        :src="employee.avatar"
        alt="Employee Avatar"
      />
      <Icon
        v-else
        size="136px"
        class="border rounded-full p-5 text-neutral-300"
        name="clarity:avatar-solid"
      />
      <div>
        <h1 class="text-neutral-800 font-bold text-3xl">
          {{ employee.first_name }} {{ employee.last_name }}
        </h1>
        <div class="my-5">
          <p>
            <span>
              <Icon name="material-symbols:mail-outline" />
              {{ employee.email }}</span
            >
          </p>
          <p>
            <Icon name="ic:baseline-phone" /> <span>{{ employee.phone }}</span>
          </p>
        </div>
        <nuxt-link
          class="border flex justify-center items-center gap-5 p-2 rounded hover:shadow"
          to="/"
        >
          <Icon name="iconoir:home" />
          <span>Back to home</span>
        </nuxt-link>
      </div>
    </div>
  </section>

  <section
    class="flex items-center mx-auto flex-col p-5 border w-1/2 rounded-es-md rounded-ee-md"
    v-else
  >
    <h1 class="text-neutral-800 text-3xl p-5 font-bold">Employee not found</h1>
    <nuxt-link
      class="text-lg flex items-center gap-2 shadow-sm border px-5 py-2 hover:shadow-md"
      to="/"
      ><Icon name="iconoir:home" /> <span>Back to home</span></nuxt-link
    >
  </section>
</template>
