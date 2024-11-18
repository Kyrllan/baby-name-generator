<script setup>
const options = reactive({
  gender: "Girl",
  popularity: "Unique",
  length: "Short",
});
</script>

<template>
  <div class="container">
    <h1>Baby Name Generator</h1>
    <p>Choose your options and click the "Find Names" buttom below</p>
    <div class="options-container">
      <div class="option-container">
        <h4>1) Choosse a Gender</h4>
        <div class="option-buttons">
          <button
            @click="options.gender = 'Boy'"
            class="option option-left"
            :class="{ 'option-active': options.gender === 'Boy' }"
          >
            Boy
          </button>
          <button
            @click="options.gender = 'Unisex'"
            class="option"
            :class="{ 'option-active': options.gender === 'Unisex' }"
          >
            Unisex
          </button>
          <button
            @click="options.gender = 'Girl'"
            class="option option-right"
            :class="{ 'option-active': options.gender === 'Girl' }"
          >
            Girl
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>2) Choosse the name's popularity</h4>
        <div class="option-buttons">
          <button
            @click="options.popularity = 'Trendy'"
            class="option option-left"
            :class="{ 'option-active': options.popularity === 'Trendy' }"
          >
            Trendy
          </button>
          <button
            @click="options.popularity = 'Unique'"
            class="option option-right"
            :class="{ 'option-active': options.popularity === 'Unique' }"
          >
            Unique
          </button>
        </div>
      </div>
      <div class="option-container">
        <h4>3) Choosse the name's length</h4>
        <div class="option-buttons">
          <button
            @click="options.length = 'Long'"
            class="option option-left"
            :class="{ 'option-active': options.length === 'Long' }"
          >
            Long
          </button>
          <button
            @click="options.length = 'All'"
            class="option"
            :class="{ 'option-active': options.length === 'All' }"
          >
            All
          </button>
          <button
            @click="options.length = 'Short'"
            class="option option-right"
            :class="{ 'option-active': options.length === 'Short' }"
          >
            Short
          </button>
        </div>
      </div>
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
