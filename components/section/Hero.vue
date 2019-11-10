<template>
  <section class="hero">
    <Titulo texto="Focinhos Anônimos" />
  </section>
</template>

<script>
import Titulo from '@/components/Titulo.vue';
export default {
  components: {
    Titulo,
  }
}
</script>

<style>

.hero {
  width: 100vw;
  height: calc(100vh - 100px);
  background-color: var(--color-background);

  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 40px 20px;

}

</style>