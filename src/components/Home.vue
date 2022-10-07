<script setup lang="ts">
import Layout from './Layout.vue';
import Header from './Header.vue';
import Resume from './Resume/Index.vue';
import Movements from './Movements/Index.vue';
interface movement {
  id: number,
  title: string,
  description: string,
  amount: number,
}
const movements: movement[] = [
  {
    id: 1,
    title: "Movimiento",
    description: "Deposito de salario",
    amount: 1000,
  },
  {
    id: 2,
    title: "Movimiento 1",
    description: "Deposito de honorarios",
    amount: 500,
  },
  {
    id: 3,
    title: "Movimiento 3",
    description: "Comida",
    amount: -100,
  },
  {
    id: 4,
    title: "Movimiento 4",
    description: "Colegiatura",
    amount: 1000,
  },
  {
    id: 5,
    title: "Movimiento 5",
    description: "Reparación equipo",
    amount: 1000,
  },
]
</script>

<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume :label="new Date()" :total-amount="10000" :amount="3">
        <template #graphic>
          graphic
        </template>
        <template #action>
          action
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movements" />
    </template>
  </Layout>
</template>