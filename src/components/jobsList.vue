<template>
  <div class="container mx-auto p-4">
    <h2 class="text-2xl font-bold mb-4">Lista de Trabajos</h2>
    <p class="mb-6">Ordenar por: {{ order }}</p>
    <transition-group name="list" tag="div" class="space-y-4">
      <div
        v-for="job in orderJobs"
        :key="job.id"
        class="flex bg-white shadow-md rounded-lg overflow-hidden"
      >
        <div class="p-4 flex-grow">
          <h3 class="text-xl font-semibold mb-2">
            {{ job.title }} en {{ job.location }}
          </h3>
          <div class="text-gray-700 mb-2">
            <span class="font-medium">Salario:</span> {{ job.salary }}
          </div>
          <div class="description text-gray-600">
            <p>
              Lorem ipsum dolor sit amet, consectetur adipisicing elit. Neque
              repellendus obcaecati a iusto. Culpa error, ipsam dolores dicta
              placeat obcaecati! Ad est quis enim officia similique culpa odio
              magni quos!
            </p>
          </div>
        </div>
      </div>
    </transition-group>
  </div>
</template>
<script lang="ts">
import { defineComponent, PropType, computed } from "vue";
import OrderTerm from "../types/orderTerm.ts";
import Job from "./types/jobs.ts";

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
  setup(props) {
    const orderJobs = computed(() => {
      return [...props.jobs].sort((a, b) => {
        if (props.order === "title") {
          return a.title.localeCompare(b.title);
        }
        if (props.order === "location") {
          return a.location.localeCompare(b.location);
        }
        if (props.order === "salary") {
          return a.salary - b.salary;
        }
        return 0;
      });
    });
    return {
      orderJobs,
    };
  },
});
</script>

<style>
.list-move {
  transition: transform 1s;
}
</style>
