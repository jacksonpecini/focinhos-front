<template>
  <section class="hero">
    <Titulo texto="Focinhos Anônimos" />
    <div class="hero__card">
      <div class="card__content">
        <img class="card__image" src="~/assets/dog.png" alt="">
        <img class="card__image" src="~/assets/cat.png" alt="">
        <Dialogo texto="Eu e meus amigos estávamos te esperando!" customClass="bottom-right" />
        <Dialogo texto="Eu e meus amigos estávamos te esperando!" customClass="top-left" />
      </div>
    </div>
  </section>
</template>

<script>
import Titulo from '@/components/Titulo.vue';
import Dialogo from '@/components/Dialogo.vue';
export default {
  components: {
    Titulo,
    Dialogo,
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

.hero__card {
  width: 500px;
  height: 200px;
  background-color: var(--color-primary);
  border-radius: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 40px;
}

.card__content {
  width: 80%;
  height: 70%;
  background-color: var(--color-grey);
  border-radius: 30px;
  position: relative;
}

.card__image {
  width: 135px;
  height: auto;
  position: absolute;
}

.card__image:first-of-type {
  bottom: 0;
  left: 40px;
}

.card__image:last-of-type {
  top: 0;
  right: 40px;
}

.dialogo:first-of-type {
  position: absolute;
  top: 50%;
  left: 0;
  transform: translateY(-50%) translateX(-90%);
}

.dialogo:last-of-type {
  position: absolute;
  top: 50%;
  right: 0;
  transform: translateY(-50%) translateX(90%);
}

</style>