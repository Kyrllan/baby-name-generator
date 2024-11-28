<template>
  <div class="card">
    <h3>{{ name }}</h3>
    <p @click="$emit('remove')">x</p>
  </div>
</template>

<script setup lang="ts">
interface NameProps {
  name: string;
}

defineProps<NameProps>();
defineEmits(["remove"]);
</script>

<style scoped>
.card {
  background-color: rgb(27, 60, 138);
  color: white;
  border-radius: 1rem;
  padding: 1rem;
  position: relative;
}

.card p {
  position: absolute;
  top: -10px;
  right: 10px;
  cursor: pointer;
  color: rgba(255, 255, 255, 0.178);
}
</style>
