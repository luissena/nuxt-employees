<script setup lang="ts">
const $router = useRouter();
const employee = reactive({
  first_name: "",
  last_name: "",
  email: "",
  phone: "",
});

const messageError = ref("");
const isLoading = ref(false);

const validator = computed(() => {
  if (employee.first_name === "") {
    messageError.value = "First name is required";

    document.getElementById("first_name")?.focus();
    return false;
  }
  if (employee.last_name === "") {
    messageError.value = "Last name is required";
    document.getElementById("last_name")?.focus();
    return false;
  }
  if (employee.email === "") {
    messageError.value = "Email is required";
    document.getElementById("email")?.focus();
    return false;
  }

  if (employee.phone === "") {
    messageError.value = "Phone is required";
    document.getElementById("phone")?.focus();
    return false;
  } else {
    return true;
  }
});

const onSubmit = async () => {
  isLoading.value = true;
  if (!validator.value) {
    isLoading.value = false;
    return;
  }
  const { error } = await useFetch("http://localhost:3000/employees", {
    method: "POST",
    body: employee,
    headers: {
      "Content-Type": "application/json",
    },
  });
  if (error.value) {
    messageError.value = error.value.message;
  } else {
    $router.push("/");
    window.alert("Employee created successfully");
  }

  isLoading.value = false;
};
</script>

<template>
  <Title>Create a new employee</Title>
  <section class="mx-auto p-5 max-w-7xl">
    <h1
      class="font-bold p-5 text-3xl text-center md:text-left md:w-2/3 mx-auto"
    >
      Create a new employee
    </h1>

    <form
      @submit.prevent="onSubmit"
      action="POST"
      class="grid grid-cols-2 gap-2 p-5 justify-center md:w-2/3 mx-auto"
    >
      <fieldset class="flex flex-col col-span-2 md:col-span-1">
        <label for="first_name">First Name</label>
        <input
          v-model="employee.first_name"
          placeholder="John "
          class="border px-2 py-1 rounded"
          type="text"
          id="first_name"
          name="first_name"
        />
      </fieldset>
      <fieldset class="flex flex-col col-span-2 md:col-span-1">
        <label for="first_name">Last Name</label>
        <input
          placeholder=" Doe"
          class="border px-2 py-1 rounded"
          type="text"
          id="last_name"
          name="last_name"
          v-model="employee.last_name"
        />
      </fieldset>

      <fieldset class="flex flex-col col-span-2">
        <label for="email">Email</label>
        <input
          class="border px-2 py-1 rounded"
          placeholder="johndoe@email.com"
          v-model="employee.email"
          id="email"
          name="email"
          type="email"
        />
      </fieldset>
      <fieldset class="flex flex-col col-span-2">
        <label for="phone">Phone</label>
        <input
          v-model="employee.phone"
          class="border px-2 py-1 rounded"
          placeholder="123-456-7890"
          id="phone"
          name="phone"
          type="tel"
        />
      </fieldset>
      <nuxt-link
        class="border flex justify-center items-center gap-5 p-2 rounded hover:shadow col-span-2 md:col-span-1"
        to="/"
      >
        <Icon name="iconoir:home" />
        <span>Back to home</span>
      </nuxt-link>
      <button
        v-if="!isLoading"
        type="submit"
        class="shadow text-gray-600 font-semibold flex justify-center items-center gap-5 bg-[#00DC82] hover:bg-[#00ff99] p-2 rounded col-span-2 md:col-span-1"
      >
        <Icon name="gridicons:create" />

        Create
      </button>
      <button
        v-else
        disabled
        class="cursor-wait shadow text-gray-600 font-semibold flex justify-center items-center gap-5 bg-[#00ff99] p-2 rounded col-span-2 md:col-span-1"
      >
        <Icon name="formkit:spinner" class="animate-spin" size="25px" />
      </button>

      <p class="text-red-500 text-center col-span-2">{{ messageError }}</p>
    </form>
  </section>
</template>
