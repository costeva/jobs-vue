<template>
  <div>
    <h2>Jobs List</h2>
    <p>Order by: {{ order }}</p>
    <ul>
      <li v-for="job in jobs" :key="job.id">
        <h3>{{ job.title }} in {{ job.location }}</h3>
        <div class="salary">Salary: {{ job.salary }}</div>
        <div class="desciption">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Neque
            repellendus obcaecati a iusto. Culpa error, ipsam dolores dicta
            placeat obcaecati! Ad est quis enim officia similique culpa odio
            magni quos!
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, Prop, PropType } from "vue";
import OrderTerm from "../types/orderTerm";
import Job from "./types/jobs";

export default defineComponent({
  name: "component-jobs-list",
  props: {
    jobs: {
      type: Array as PropType<Job[]>,
      required: true,
    },
    order: {
      type: String as PropType<OrderTerm>,
      required: true,
    },
  },
  setup() {},
});
</script>
