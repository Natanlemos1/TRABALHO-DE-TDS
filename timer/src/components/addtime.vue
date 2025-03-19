<template>
  <button @click="$emit('add-minute')">Adicionar 1 Minuto</button>
</template>

<script>
export default {
  name: "AddTime",
};
</script>

<style scoped>
button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  margin-top: 10px;
}
button:hover {
  background-color: #0056b3;
}
</style>
