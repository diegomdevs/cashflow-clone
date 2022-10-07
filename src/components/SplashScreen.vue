<script setup lang="ts">

</script>
<template>
  <main class="splashscreen-container">
    <section class="splashscreen">
      <picture class="splashscreen--icon-container">
        <img class="icon" src="../assets/cashflow-icon.svg" alt="cashflow-icon" srcset="" />
      </picture>
      <section class="splashscreen--title-container">
        <h1 class="title">
          <span>
            Cash
          </span>
          Flow
        </h1>
      </section>

    </section>
  </main>
</template>
<style scoped>
main.splashscreen-container>section.splashscreen {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 100%;
}

main.splashscreen-container>section.splashscreen>section.splashscreen--title-container>h1.title {
  color: var(--brand-blue);
}

main.splashscreen-container>section.splashscreen>section.splashscreen--title-container>h1.title>span {
  color: var(--brand-green);
}
</style>