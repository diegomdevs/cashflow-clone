<script setup lang="ts">
import { ref, Ref } from 'vue';
import Modal from './Modal.vue';
const showModal = ref(false);
const [title, description, movementType] = [ref(''), ref(''), ref('')];
const amount = ref(0);
const submit = () => {
  showModal.value = !showModal;
}
</script>
<template>
  <button @click="showModal = !showModal">
    Agregar movimiento
  </button>
  <Teleport to="#app">
    <Modal v-show="showModal" @close="showModal = false">
      <form @submit.prevent="submit">
        <section class="field">
          <label for="">
            Title
          </label>
          <input type="text" v-model="title">
        </section>
        <section class="field">
          <label for="">
            Amount
          </label>
          <input type="number" v-model="amount">
        </section>
        <section class="field">
          <label for="">
            Description
          </label>
          <textarea v-model="description" rows="4"></textarea>
        </section>
        <section class="field">
          <label for="">
            Movement type
          </label>
          <label class="radio-label" for="">
            <input type="radio" v-model="movementType" value="income">
            <span>
              Income
            </span>
            <input type="radio" v-model="movementType" value="spending">
            <span>
              Spending
            </span>
          </label>
        </section>
        <section>
          <button class="action">
            Add movement
          </button>
        </section>
      </form>
    </Modal>
  </Teleport>
</template>

<style scoped>
button {
  color: white;
  font-size: 1.25rem;
  background-color: var(--brand-blue);
  border: none;
  width: 100%;
  padding: 24px 60px;
  border-radius: 60px;
  box-sizing: border-box;
}

form {
  font-size: 1.24rem;
  width: 100%;
}

form .action {
  padding: 0 24px;
}

.field {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  padding: 16px 24px;
}

label {
  margin-bottom: 8px;
}

input,
textarea {
  font-size: 1.24rem;
  border: 2px solid var(--brand-blue);
  border-radius: 8px;
  padding: 8px;
}

input[type="number"] {
  text-align: right;
}

.radio-label {
  display: flex;
  align-items: center;
  margin-top: 8px;
}

.radio-label span {
  margin-top: 4px;
  margin-left: 8px;
}

input[type="radio"] {
  appearance: none;
  width: 1.24rem;
  height: 1.24rem;
  color: var(--brand-blue);
  border: 2px solid var(--brand-blue);
  border-radius: 50%;
}

input[type="radio"]:checked {
  background-color: var(--brand-blue);
}
</style>