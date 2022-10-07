<script setup lang="ts">
const reload = () => {
  location.reload();
}
</script>

<template>
  <section>
    <picture>
      <img @click="reload" src="../assets/cashflow-icon.svg" alt="cashflow-icon">
    </picture>
    <h1><span>Cash</span>Flow</h1>
  </section>
</template>

<style scoped>
section:only-child:only-of-type {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 100vw;
}

section:only-child:only-of-type>picture>img,
section:only-child:only-of-type>h1>span {
  width: 48px;
}

section>h1 {
  font-size: 1.4rem;
  color: var(--brand-blue);
  margin-right: 20%;

}

section>h1>span {
  color: var(--brand-green);
}
</style>