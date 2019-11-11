<template>
<div class="doar">
    <Header />
    <main class="main">
        <Titulo texto="Doação"/>
        <info>
            <div class="adotar__content">

            </div>
        </info>
    
    </main>
</div>
  
</template>

<script>
import Header from '@/components/common/Header.vue';
import Titulo from '@/components/Titulo.vue';
import Cards from '@/components/Cards.vue';
export default {
    components: {
        Header,
        Titulo,
        Cards,
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