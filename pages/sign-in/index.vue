<template>
  <BaseLayout>
    <div class="sign-in">
      <h1>Sign In</h1>
      <form action="">
        <div class="input-group">
          <label for="email">Email</label>
          <input type="email" id="email" name="email" />
        </div>
        <div class="input-group">
          <label for="password">Password</label>
          <input type="password" id="password" name="password" />
        </div>
        <div class="input-group">
          <button type="submit" @click="handleSubmit">Sign In</button>
        </div>
      </form>
    </div>
  </BaseLayout>
</template>

<style scoped>
.input-group {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
}

.input-group label {
  margin-bottom: 0.5rem;
}

.input-group input {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.input-group button {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: #ccc;
  cursor: pointer;
}
</style>

<script setup lang="ts">
import BaseLayout from "../../layouts/BaseLayout.vue";

const handleSubmit = (event: MouseEvent) => {
  event.preventDefault();
  alert("Sign In");
};
</script>
