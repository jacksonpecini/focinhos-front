<template>
  <div class="about">
    <Header />
    <main class="main">
        <Titulo texto="Sobre Nós" />
        <Info>
            <div class="about__content">
                <p class="faq__text">
                    A ideia principal utilizada para a criação do site é não ter contato visual
                    com o pet, ao invés disso é feito uma análise de perfis
                    baseado em dados dispondo os pets que possivelmente se adaptaria melhor com cada ambiente e cada familia.
                    Cada doador disponibilizará uma história sobre o pet para que o usuário saiba um pouco sobre ele e poder fazer sua escolha dentro do que o lhe foi disposto.
                    Viabilizando assim, adoções menos estereotipadas e possivelmente mais assertivas.
                </p>
                    <p class="faq__text"> tipo de adoção passaria por um período de adaptação
                    inicial onde o pet, após ser escolhido sem mostrar uma imagem se quer, 
                    iria para a casa do adotante por um período de duas semanas onde, após esse período, 
                    o possível dono daria o feedback de como foi o processo e se continuará com a adoção definitiva ou não.
                    </p>
                   <p class="faq__text"> Dessa forma, daríamos chance de conhecer o jeitinho do seu possível novo amigo, 
                    evitando adoções impulsivas e rejeições que levariam o pet às ruas novamente. 
                    Também dando a chance de evitar que primeiras impressões atrapalhe uma grande amizade.
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