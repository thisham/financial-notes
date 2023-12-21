<template>
  <BaseLayout>
    <div class="">
      <!-- table view, contains date, debit, credit, total -->
      <h1>Closings</h1>
      <div class="heading-toolbar-wrapper">
        <div class="heading-button-bar">
          <router-link :to="`/closings/${route.params.id}/update`"
            >Update Closing</router-link
          >
        </div>
      </div>
      <table>
        <thead>
          <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Nominal</th>
            <th>Note</th>
          </tr>
        </thead>
        <tbody>
          <!-- loop through the data and display it in the table -->
          <tr v-for="item in data" :key="item.id">
            <td>{{ item.name }}</td>
            <td>{{ item.type }}</td>
            <td>{{ item.nominal }}</td>
            <td>{{ item.note }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </BaseLayout>
</template>

<script setup lang="ts">
import BaseLayout from "../../../layouts/BaseLayout.vue";
import { useRoute } from "vue-router";

const route = useRoute();
console.log("route.params.id", route.params.id);

// mock data for the table
const data = [
  {
    id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
    name: "2021-01-01",
    type: "debit",
    nominal: 100000,
    note: "test",
  },
  {
    id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
    name: "2021-01-01",
    type: "debit",
    nominal: 100000,
    note: "test",
  },
  {
    id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
    name: "2021-01-01",
    type: "debit",
    nominal: 100000,
    note: "test",
  },
  {
    id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
    name: "2021-01-01",
    type: "debit",
    nominal: 100000,
    note: "test",
  },
  {
    id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
    name: "2021-01-01",
    type: "debit",
    nominal: 100000,
    note: "test",
  },
  {
    id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
    name: "2021-01-01",
    type: "debit",
    nominal: 100000,
    note: "test",
  },
];
</script>
