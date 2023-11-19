<script setup>
import { ref, reactive } from 'vue';

const counters = reactive([
  { name: 'лечение', count: ref(0), max_count: 15000 },
  { name: 'PlayStation 6', count: ref(0), max_count: 10000 },
  { name: 'Xbox One X', count: ref(0), max_count: 5000 },
  { name: 'iPhone 15 Pro Max', count: ref(0), max_count: 10000 },
  { name: 'дом в Штатах', count: ref(0), max_count: 15000 },
  { name: 'помощь бездомным', count: ref(0), max_count: 10000 },
  { name: 'строительство школы', count: ref(0), max_count: 30000 },
]);

const decrementCount = (targetCounter) => {
  if (targetCounter.count > 0) {
    targetCounter.count -= 500;
  }
};

const incrementCount = (targetCounter) => {
  if (targetCounter.count < targetCounter.max_count) {
    targetCounter.count += 500;
  }
};
</script>

<template>
  <div class="container">
    <p class="container-title">Актуальные пожертвования</p>
    <div v-for="counter in counters" :key="counter.name">
      <p class="count-text">
        Собрано на {{ counter.name }}: 
        <span class="count-value">{{ counter.count }} &#8381;</span>
        <br>
        <progress :value="counter.count" :max="counter.max_count"></progress>
      </p>
      <div class="container-buttons">
        <button class="container-button" @click="decrementCount(counter)">-</button>
        <button class="container-button" @click="incrementCount(counter)">+</button>
      </div>
    </div>
  </div>
  
</template>

<style scoped>
progress {
    width: 60%;
    max-width: 400px;
    min-width: 150px;
    /* accent-color: rgb(88, 88, 88); */
}

.container {
  margin: 50px auto; 
  padding: 5px;
  text-align: center;
  display: flex;
  flex-direction: column;
}

.count-text {
  margin-top: 100px;
  margin-bottom: 10px;
  font-size: calc(1em + 1vw);
}

/* .count-text:first-of-type {
  margin-top: 20px;
} */

.count-value {
  color: gold;
}

.container-button {
  font-size: calc(1em + .5vw);
  background-color: rgb(224, 224, 224);
  border-radius: 0.5em;
  border: 0;
  margin: 0px 5px 0px 5px;
  cursor: pointer;
  width: 3vw; /* 5% от ширины видимой области */
  height: 3vw;
  min-width: 50px;
  min-height: 50px;
  max-width: 90px;
  max-height: 90px;
}

.container-button:hover {
    background-color: rgb(202, 202, 202);
}
</style>