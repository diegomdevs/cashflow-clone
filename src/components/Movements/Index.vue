<script setup lang="ts">
import { toRefs } from 'vue';
import Movement from './Movement.vue';

interface movement {
  id: number,
  title: string,
  description: string,
  amount: number,
}
interface Props {
  movements: movement[],
}
const props = defineProps<Props>()
const { movements } = toRefs(props)
const remove = (id: string) => {
  console.log('remove', id)
}
</script>

<template>
  <section class="movements">
    <h1 class="title">
      Historial
    </h1>
    <section class="content">
      <Movement v-for="movement in movements" :key="movement.id" :title="movement.title" :amount="movement.amount"
        :description="movement.description" :id="movement.id" @remove="remove"> </Movement>
    </section>
  </section>
</template>

<style scoped>
.movements {
  max-height: 100%;
  padding: 0 8px;
  margin-bottom: 14px;
}

.title {
  margin: 8px 16px 24px 16px;
  color: var(--brand-blue);
}

.content {
  max-height: 68vh;
  display: flex;
  flex-direction: column;
  gap: 8px;
  overflow-y: scroll;
}
</style>