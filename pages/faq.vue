<template>
  <div class="faq">
    <Header />
    <main class="main">
        <Titulo texto="FAQ" />
        <Info>
            <div class="faq__content">
                <h3 class="faq__title">
                    Para mais informações
                </h3>
                <p class="faq__text">
                    Jack Pecini
                </p>
                <p class="faq__text">
                    E-mail: jacksonpecini10@gmail.com
                </p>
                <p class="faq__text">
                    Dhiessica
                </p>
                <p class="faq__text">
                    E-mail: XXXXXXXXXXXXXXX
                </p>
                <p class="faq__text">
                    Bianca
                </p>
                <p class="faq__text">
                    E-mail: XXXXXXXXXXXXXXX
                </p>
            </div>
        </Info>
    </main>
  </div>
</template>

<script>
import Header from '@/components/common/Header.vue';
import Titulo from '@/components/Titulo.vue';
import Info from '@/components/Info.vue';
export default {
    components: {
        Header,
        Titulo,
        Info,
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

.faq__content {
    font-family: Roboto, sans-serif;
}

.faq__title {
    font-size: 20px;
}

.faq__text {
    font-size: 16px;
    margin: 20px 0;
}

</style>