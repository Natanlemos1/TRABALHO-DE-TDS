<template>
  <button @click="$emit('reset-timer')">Encerrar Timer</button>
</template>

<script>
export default {
  name: "Encerrar",
};
</script>

<style scoped>
button {
  background-color: #dc3545;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  margin-top: 10px;
}
button:hover {
  background-color: #b52b3a;
}
</style>
