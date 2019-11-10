<template>
  <div :class="`dialogo arrow--${customClass}`">
    <p class="dialogo__texto">
      {{texto}}
    </p>
  </div>
</template>

<script>
export default {
  props: [
    "texto",
    "customClass"
  ]
}
</script>

<style>

.dialogo {
  padding: 20px;
  max-width: 230px;
  background-color: #fff;
  border-radius: 20px;
  position: relative;
}

.dialogo::after {
  content: '';
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
  width: 30px;
  height: 30px;
  background-color: #fff;
  position: absolute;
}

.arrow--bottom-right::after {
  bottom: 5px;
  right: -10px;
}

.arrow--top-left::after {
  top: 5px;
  left: -10px;
  transform: rotate(180deg);
}

.dialogo__texto {
  font-size: 20px;
  text-align: center;
}

</style>