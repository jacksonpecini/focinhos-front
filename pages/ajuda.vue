<template>
  <div class="ajuda">
    <Header />
    <main class="main">
        <Titulo texto="Ajuda" />
        <Info :withBackground="true">
            <div class="about__content">
                <p class="faq__text">
                    PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER -
                    PREENCHER - PREENCHER - PREENCHER - PREENCHER 
                </p>
                    <p class="faq__text"> 
                    PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER -
                    PREENCHER - PREENCHER - PREENCHER - PREENCHER 
                    </p>
                   <p class="faq__text">
                    PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER - PREENCHER -
                    PREENCHER - PREENCHER - PREENCHER - PREENCHER 
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

.about__content {
    font-family: Roboto, sans-serif;
  
}


.about__text {
    font-size: 16px;
    margin: 20px 0;
}

</style>