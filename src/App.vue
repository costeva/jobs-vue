<template>
  <div>
    <button @click="handleClick('title')">Order by title</button>
    <button @click="handleClick('location')">Order by location</button>
    <button @click="handleClick('salary')">Order by salary</button>
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
        location: "Madrid",
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
