<template>
  <div class="base">
    <slot />
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}

.base {
  width: 100vw;
  min-height: 100vh;
  background-color: #f5f5f5;
  padding: 1rem;
}

h1 {
  margin-bottom: 1rem;
}
</style>
