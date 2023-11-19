<script setup>
import { ref, reactive } from 'vue';
import { useFetch } from '@vueuse/core';

const url = "http://127.0.0.1:8000/main";
const { data } = useFetch(url, { refetch: true }).json();
const counters = reactive(data);

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
    <p class="container-title">Актуальные пожертвования в Москве</p>
    <div v-for="(counter, index) in counters" :key="counter.title" :style="{ marginTop: index === 0 ? '10px' : '80px' }">
      <p class="count-text">
        Собрано на {{ counter.title }}: 
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
    width: 70vw;
    max-width: 350px;
    /* accent-color: rgb(88, 88, 88); */
}

.container {
  margin: 50px auto; 
  padding: 5px;
  text-align: center;
  display: flex;
  flex-direction: column;
}

.container-title {
  padding: 1em 0 0 0;
  font-weight: 500;
  font-size: calc(.8em + 1.7vw);
}

.count-text {
  margin-bottom: 10px;
  font-size: calc(.7em + 1.3vw);
}

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
  width: 30vw;
  height: 30vw;
  max-width: 50px;
  max-height: 50px;
}

.container-button:hover {
    background-color: rgb(202, 202, 202);
}
</style>