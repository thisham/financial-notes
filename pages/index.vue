<template>
  <div>
    <p>My Nuxt.js app {{ state.count }}</p>

    <button v-on:click="state.increase()">inc</button>

    <p>My Nuxt.js app {{ form.name }}</p>
    <form action="">
      <label for="name">Name</label>
      <input type="text" v-model="form.name" id="name" name="name" />
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from "vue";

const state = reactive({
  count: 0,
  increase() {
    state.count++;
  },
});

const form = ref({
  name: "nuxt",
});
</script>
