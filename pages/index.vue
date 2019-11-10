<template>
  <div class="home">
    <Header />
    <main class="main">
      <Hero />
    </main>
  </div>
</template>

<script>
import Header from '@/components/common/Header.vue';
import Hero from '@/components/section/Hero.vue';
export default {
  components: {
    Header,
    Hero,
  }
}
</script>

<style>
</style>
