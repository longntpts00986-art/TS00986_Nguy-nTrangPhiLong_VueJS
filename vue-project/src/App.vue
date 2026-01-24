<script setup>
import Tang34 from './components/Tang34.vue'
import Bai3 from './components/Bai3.vue';
import Bai4 from './components/Bai4.vue';
</script>

<template>
  <Tang34/> 
  <hr> 
  <Bai3/> 
  <hr>
  <Bai4/>
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
