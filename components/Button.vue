<template>
  <a :href="url" :class="`btn bg--${backgroundColor} text--${textColor}`">
    {{texto}}
  </a>
</template>

<script>
export default {
  props: [
    "url",
    "texto",
    "backgroundColor",
    "textColor"
  ]
}
</script>

<style>

.btn {
  background-color: var(--color-highlight);
  color: var(--color-orange);
  padding: 5px 40px;
  font-size: 25px;
  font-weight: bold;
  text-transform: uppercase;
  border-radius: 15px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.bg--orange {
  background-color: var(--color-orange);
}

.text--yellow {
  color: var(--color-highlight);
}

</style>