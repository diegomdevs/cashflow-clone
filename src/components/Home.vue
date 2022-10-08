<script setup lang="ts">
import Layout from './Layout.vue';
import Header from './Header.vue';
import Resume from './Resume/Index.vue';
import Movements from './Movements/Index.vue';
import Action from './Action.vue';
import Graphic from './Graphic.vue';
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
const amounts: number[] = [100, 200, 500, 200, -400, -600, -300, 0, 300, 500];
</script>

<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume :label="new Date()" :total-amount="10000" :amount="3">
        <template #graphic>
          <Graphic :amounts="amounts" />
        </template>
        <template #action>
          <Action />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movements" />
    </template>
  </Layout>
</template>