<script setup>
import LinkingTool from './components/LinkingTool.vue';

</script>

<template>
  <header>
 
    <div class="wrapper">
      <img src="./assets/logo.png" alt="Vue logo" class="logo" />
      <h1 class="text-3xl font-bold mb-4">Nodots - tool voor genereren van link voor campagnes</h1>
    </div>
  </header>

  <main class="">
<LinkingTool />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
