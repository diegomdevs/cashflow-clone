
<script setup lang="ts">
import { computed, toRefs, Ref } from 'vue';

interface Props {
  amounts: number[]
};
const props = defineProps<Props>();

const { amounts } = toRefs(props);

const amountToPixels = () => {
  const min = Math.min(...amounts.value);
  const max = Math.max(...amounts.value);

  return `${min}, ${max}`
}

const points = computed(() => {
  const total = amounts.value.length;

  return Array(total).fill(100).reduce((points, amount, i) => {
    const x = (300 / total) * (i + 1);
    const y = amountToPixels(amount)
    return `${points} ${x},${y}`;
  }, '0, 100')
})
</script>
<template>
  <section>
    <svg viewBox="0 0 300 200">
      <line stroke="#c4c4c4" stroke-width="2" x1="0" y1="100" x2="300" y2="100" />
      <polyline fill="none" stroke="#0689B0" stroke-width="2" :points="points" />
      <line stroke="#0689B0" stroke-width="2" x1="200" y1="0" x2="200" y2="200" />
    </svg>
    <p>Last 30 days</p>
  </section>
</template>
<style scoped>
svg {
  width: 100%;
}

p {
  text-align: center;
}
</style>