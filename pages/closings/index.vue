<template>
  <BaseLayout>
    <div class="">
      <!-- table view, contains date, debit, credit, total -->
      <h1>Closings</h1>
      <div class="heading-toolbar-wrapper">
        <!-- filter monthly, month input, default this month -->
        <input
          type="month"
          id="month"
          name="month"
          class="filter"
          :value="new Date().toISOString().slice(0, 7)"
          v-on:change="handleMonthFilterChange"
        />

        <div class="heading-button-bar">
          <router-link to="/closings/create">Create Closing</router-link>
        </div>
      </div>
      <table>
        <thead>
          <tr>
            <th>Date</th>
            <th>Debit</th>
            <th>Credit</th>
            <th>Total</th>
          </tr>
        </thead>
        <tbody>
          <!-- loop through the data and display it in the table -->
          <tr v-for="item in data" :key="item.date">
            <td>
              <router-link :to="`/closings/${item.id}`">{{
                item.date
              }}</router-link>
            </td>
            <td class="numeric">{{ item.debit }}</td>
            <td class="numeric">{{ item.credit }}</td>
            <td class="numeric">{{ item.total }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </BaseLayout>
</template>

<script setup lang="ts">
import BaseLayout from "../../layouts/BaseLayout.vue";

// change handler for month input
const handleMonthFilterChange = (event: Event) => {
  console.log(event);
};

// mock data for the table
const data = [
  {
    id: "2fbfc891-1ad5-4963-8f8f-2d87142c73b5",
    date: "2021-01-01",
    debit: 100,
    credit: 0,
    total: 100,
  },
  {
    id: "67a2ba1b-a3fa-4c58-aa98-f4d020259de4",
    date: "2021-01-02",
    debit: 0,
    credit: 50,
    total: 50,
  },
  {
    id: "48ff0e43-5262-4794-a4ff-18ba19cc3ad6",
    date: "2021-01-03",
    debit: 0,
    credit: 50,
    total: 0,
  },
];
</script>
