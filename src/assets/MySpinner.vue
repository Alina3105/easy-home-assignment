<template>
  <div class="rainbow-spinner"></div>
</template>

<script setup></script>

<style scoped>
.rainbow-spinner {
  border: 8px solid transparent;
  border-top: 8px solid red;
  border-radius: 50%;
  width: 60px;
  height: 60px;
  animation: spin 1.5s linear infinite, rainbow 5s linear infinite;
  margin: 50px auto;
}
@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
@keyframes rainbow {
  0% {
    border-top-color: red;
  }
  14% {
    border-top-color: orange;
  }
  28% {
    border-top-color: yellow;
  }
  42% {
    border-top-color: green;
  }
  57% {
    border-top-color: blue;
  }
  71% {
    border-top-color: indigo;
  }
  85% {
    border-top-color: violet;
  }
  100% {
    border-top-color: red;
  }
}
</style>
