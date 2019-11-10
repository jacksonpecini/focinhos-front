<template>
  <div class="faq">
    <Header />
    <main class="main">
        <Titulo texto="FAQ" />
    </main>
  </div>
</template>

<script>
import Header from '@/components/common/Header.vue';
import Titulo from '@/components/Titulo.vue';
export default {
    components: {
        Header,
        Titulo,
    }
}
</script>

<style>

.main{
    display:flex;
    flex-direction: column;
    align-items: center;
    background-color: var(--color-background);
    min-height: 100vh;
}

.titulo{
    margin:40px 0;
}

</style>