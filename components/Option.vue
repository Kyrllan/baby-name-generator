<script setup lang="ts">
import type { Gender, Length, Popularity } from "~/data";

interface OptionProps {
  option: {
    title: string;
    category: string;
    buttons: Gender[] | Popularity[] | Length[];
  };
  options: {
    gender: Gender;
    popularity: Popularity;
    length: Length;
  };
}

defineProps<OptionProps>();

const emit = defineEmits(["update:options"]);
</script>

<template>
  <div class="option-container">
    <h4>{{ option.title }}</h4>
    <div class="option-buttons">
      <button
        v-for="(button, i) in option.buttons"
        :key="i"
        class="option"
        :class="{
          'option-active': options[option.category] === button,
          'option-left': i === 0,
          'option-right': i === option.buttons.length - 1,
        }"
        @click="options[option.category] = button"
      >
        {{ button }}
      </button>
    </div>
  </div>
</template>

<style scoped>
.option-container {
  margin-bottom: 2rem;
}

.option {
  background-color: white;
  outline: 0.15rem solid rgb(249, 87, 89);
  border: none;
  padding: 0.75rem;
  width: 12rem;
  font-size: 1rem;
  color: rgb(27, 60, 138);
  font-weight: 200;
  cursor: pointer;
}

.option-left {
  border-top-left-radius: 1rem;
  border-bottom-left-radius: 1rem;
}
.option-right {
  border-top-right-radius: 1rem;
  border-bottom-right-radius: 1rem;
}

.option-active {
  background-color: rgb(249, 87, 89);
  color: white;
}
</style>
