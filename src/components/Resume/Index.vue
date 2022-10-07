<script setup lang="ts">
import { isDate } from '@vue/shared';
import { computed } from 'vue';

interface Props {
  label?: Date,
  totalAmount: number,
  amount?: number;
}
const props = defineProps<Props>()
const currencyFormatter = new Intl.NumberFormat('es-MX', {
  style: 'currency',
  currency: 'MXN'
})
const visualAmount = computed(() => {
  return props.amount !== undefined ? props.amount : props.totalAmount;
})

const visualLabel = computed(() => {
  return isDate(props.label) ? props?.label.toLocaleDateString('en-US') : 'Ahorro Total'
})

const currencyAmount = computed(() => {
  return currencyFormatter.format(visualAmount.value)
})

</script>
<template>
  <main>
    <p>
      {{ visualLabel }}
    </p>
    <h1>
      {{ currencyAmount }}
    </h1>
    <section class="graphic">
      <slot name="graphic">

      </slot>
    </section>
    <section class="action">
      <slot name="action"></slot>
    </section>
  </main>
</template>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}

h1,
p {
  margin: 0;
  text-align: center;
}

h1 {
  margin-top: 14px;
  color: var(--brand-green);
}

.graphic {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 48px 24px;
  box-sizing: border-box;
}
</style>