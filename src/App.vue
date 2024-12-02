<template>
  <div>
    <!-- Header -->
    <header class="bg-blue-600 text-white py-6 mb-8">
      <div class="container mx-auto flex items-center justify-between px-4">
        <h1 class="text-3xl font-bold">Bolsa de Trabajo</h1>
      </div>
    </header>
    <!-- Main Content -->
    <div class="container mx-auto p-4">
      <!-- Botones de ordenación -->
      <div class="flex space-x-4 mb-6 justify-center">
        <button
          @click="handleClick('title')"
          class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600"
        >
          Ordenar por título
        </button>
        <button
          @click="handleClick('location')"
          class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600"
        >
          Ordenar por ubicación
        </button>
        <button
          @click="handleClick('salary')"
          class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600"
        >
          Ordenar por salario
        </button>
      </div>
    </div>

    <!-- Lista de trabajos -->
    <list-jobs :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Job from "./types/jobs";
import listJobs from "./components/jobsList.vue";
import OrderTerm from "./types/orderTerm";
export default defineComponent({
  name: "welcome",
  components: {
    listJobs,
  },
  setup() {
    const jobs = ref<Job[]>([
      {
        id: 1,
        title: "Frontend Developer",
        location: "Zadrid",
        salary: 30000,
      },
      {
        id: 2,
        title: "Backend Developer",
        location: "Barcelona",
        salary: 40000,
      },
      {
        id: 3,
        title: "Fullstack Developer",
        location: "Valencia",
        salary: 50000,
      },
    ]);

    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return {
      order,
      jobs,
      handleClick,
    };
  },
});
</script>
