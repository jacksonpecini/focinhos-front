<template>
  <div class="titulo">
    <h1 class="titulo__texto">
      {{texto}}
    </h1>
    <span class="titulo__circulo"></span>
    <span class="titulo__circulo"></span>
    <span class="titulo__circulo"></span>
    <span class="titulo__circulo"></span>
  </div>
</template>

<script>
export default {
  props: [
    "texto"
  ]
}
</script>

<style>

.titulo {

  background-color: white;
  padding: 20px;
  width: 350px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;

}

.titulo__texto {
  font-size: 35px;
}

.titulo__circulo {
  width: 10px;
  height: 10px;
  background-color: var(--color-background);
  border-radius: 100%;
  position: absolute;
  margin: 15px;
}

.titulo__circulo:nth-of-type(1) {
  top: 0;
  left: 0;
}

.titulo__circulo:nth-of-type(2) {
  top: 0;
  right: 0;
}

.titulo__circulo:nth-of-type(3) {
  bottom: 0;
  left: 0;
}

.titulo__circulo:nth-of-type(4) {
  bottom: 0;
  right: 0;
}

</style>