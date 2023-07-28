<script setup lang="ts">
import { Employee } from "types/employee.type";

useHead({
  title: "Employees",
});

const { data: employees } = await useFetch<Employee[]>(
  "http://localhost:3000/employees"
);
</script>

<template>
  <main class="mx-auto p-5 max-w-7xl">
    <h1 class="font-bold m-5 text-3xl">Employees</h1>

    <ul class="grid sm:grid-cols-2 md:grid-cols-4 justify-center mt-5">
      <li
        class="m-5 border p-2 hover:shadow-lg"
        v-for="employee in employees"
        :key="employee.id"
      >
        <nuxt-link
          class="flex flex-col items-center"
          :to="`/employee/${employee.id}`"
        >
          <img
            v-if="employee.avatar"
            class="rounded-full border mx-auto"
            :src="employee.avatar"
            alt="Employee Avatar"
          />
          <Icon
            v-else
            size="130px"
            class="border rounded-full p-5 text-neutral-300"
            name="clarity:avatar-solid"
          />
          <p class="text-center text-lg font-semibold py-2">
            {{ employee.first_name + " " + employee.last_name }}
          </p>
        </nuxt-link>
      </li>
    </ul>
  </main>
</template>
