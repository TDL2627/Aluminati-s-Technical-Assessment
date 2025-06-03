<!-- All reasons for change and exact change details in the fixes and changes MD  ❤️ -->
<script setup lang="ts">
import { ref, computed } from "vue";

const limit = ref<number>(100);
const hoveredNumber = ref<number>(0);

const randomNumbers = computed(() => {
  const numbers: number[] = [];
  for (let i = 0; i < limit.value; i++) {
    numbers.push(i);
  }
  return numbers.sort(() => Math.random() - 0.5);
});

const hov = (num: number) => {
  console.log(num);

  hoveredNumber.value = num;
};

const reset = () => {
  hoveredNumber.value = 0;
};

const isFactor = (a: number, b: number): boolean => {
  return a % b === 0;
};
</script>

<template>
  <div>
    <h1 class="title">Factorize</h1>
    <input type="number" v-model="limit" /><br /><br />
    <div
      class="number"
      v-for="number in randomNumbers"
      :class="{  active: hoveredNumber !== 0 && isFactor(hoveredNumber, number) }"
      :key="number"
      @mouseover="hov(number)"
      @mouseout="reset"
    >
      {{ number }}
    </div>
  </div>
</template>
