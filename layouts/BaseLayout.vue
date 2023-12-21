<template>
  <div class="base">
    <div class="base-wrapper">
      <slot />
    </div>
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
  display: flex;
  justify-content: center;
  width: 100vw;
  min-height: 100vh;
  background-color: #f5f5f5;
  padding: 1rem;
}

.base-wrapper {
  width: 100%;
  max-width: 786px;
}

h1 {
  margin-bottom: 1rem;
}
</style>
