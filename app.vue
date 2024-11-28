<script setup lang="ts">
import { Gender, Popularity, Length, names } from "./data";
interface OptionsState {
  gender: Gender;
  popularity: Popularity;
  length: Length;
}

const options = reactive<OptionsState>({
  gender: Gender.GIRL,
  popularity: Popularity.UNIQUE,
  length: Length.SHORT,
});

const selectedNames = ref<string[]>([]);

const computeSelectedNames = () => {
  const filteredNames = names
    .filter((name) => name.gender === options.gender)
    .filter((name) => name.popularity === options.popularity)
    .filter((name) => {
      return options.length === Length.ALL
        ? true
        : name.length === options.length;
    });
  selectedNames.value = filteredNames.map((name) => name.name);
};

const removeName = (index: number) => {
  selectedNames.value.splice(index, 1);
};

const optionsArray = [
  {
    title: "1) Choose a Gender",
    category: "gender",
    buttons: [Gender.BOY, Gender.UNISEX, Gender.GIRL],
  },
  {
    title: "2) Choose a Popularity",
    category: "popularity",
    buttons: [Popularity.UNIQUE, Popularity.TRENDY],
  },
  {
    title: "3) Choose a Length",
    category: "length",
    buttons: [Length.ALL, Length.SHORT, Length.LONG],
  },
];
</script>

<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" buttom below</p>
    <div class="options-container">
      <Option
        v-for="option in optionsArray"
        :key="option.title"
        :option="option"
        :options="options"
      />
      <button class="primary" @click="computeSelectedNames">Find Names</button>
    </div>
    <div class="cards-container">
      <CardName
        v-for="(name, i) in selectedNames"
        :key="i"
        :name="name"
        @remove="removeName(i)"
      />
    </div>
  </div>
</template>

<style scoped>
.container {
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(27, 60, 138);
  max-width: 50rem;
  margin: 0 auto;
  text-align: center;
}

h1 {
  font-size: 3rem;
}

.options-container {
  background-color: rgb(255, 238, 236);
  border-radius: 2rem;
  padding: 1rem;
  width: 95%;
  margin: 0 auto;
  margin-top: 4rem;
  position: relative;
}

.primary {
  background-color: rgb(249, 87, 89);
  color: white;
  border-radius: 6.5rem;
  border: none;
  padding: 0.75rem 4rem;
  font-size: 1rem;
  margin-top: 1rem;
  cursor: pointer;
}

.cards-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
  padding-top: 2rem;
}
</style>
