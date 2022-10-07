<script setup lang="ts">
import { computed, toRefs } from 'vue';

interface Props {
  id: number,
  title: string,
  description: string,
  amount: number,
}

const props = defineProps<Props>()
const { title, amount, description, id } = toRefs(props)
const currencyFormatter = new Intl.NumberFormat('es-MX', {
  style: 'currency',
  currency: 'MXN'
})
const amountCurrency = computed(() => {
  return currencyFormatter.format(amount.value)
})
const emit = defineEmits(['remove'])
const remove = () => {
  emit('remove', id.value)
}
const isNegative = computed(() => { return amount.value < 0 })
</script>

<template>
  <section class="movement">
    <article class="content">
      <h4>
        {{ title }}
      </h4>
      <p>
        {{ description }}
      </p>
    </article>
    <article class="action">
      <img src="../../assets/trash-icon.svg" alt="trash-icon" @click="remove">
      <p :class="{ 'red': isNegative, 'green': !isNegative}">{{ amountCurrency }}</p>
    </article>
  </section>
</template>

<style scoped>
.movement {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 16px;
  background-color: #e6f9ff;
  border-radius: 8px;
  box-sizing: border-box;
}

.movement .content {
  width: 100%;
}

.movement .action {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  flex-direction: column;
}

h4,
p {
  margin: 0;
  padding: 0;
}

h4 {
  margin-bottom: 8px;
}

.movement .action img {
  margin-bottom: 16px;
}

.red {
  color: red;
}

.green {
  color: green;
}
</style>