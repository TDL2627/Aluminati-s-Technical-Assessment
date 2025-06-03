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
  hoveredNumber.value = num;
};

const reset = () => {
  hoveredNumber.value = 0;
};
</script>

<template>
  <div>
    <input type="number" v-model="limit" /><br /><br />
    <div
      class="number"
      v-for="number in randomNumbers"
      :class="{ active: hoveredNumber !== 0 && hoveredNumber % number === 0 }"
      :key="number"
      @mouseover="hov(number)"
      @mouseout="reset"
    >
      {{ number }}
    </div>
  </div>
</template>

