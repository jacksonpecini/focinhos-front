<template>
  <div class="info">
      <div :class="`info__content ${!withBackground && `info__content--nobg`}`">
          <slot/>
      </div>
  </div>
</template>

<script>
export default {
  props: [
    "withBackground",
    "width",
    "height",
  ]
};
</script>

<style>

.info {
  background-color: var(--color-primary);
  width: 500px;
  display: flex;
  border-radius: 25px;
  overflow: hidden;
}

.info__content {
  background-color: var(--color-grey);
  width: 100%;
  margin: 20px;
  padding: 20px;
  font-size: 20px;
  color: #fff;
  text-align: center;
  border-radius: 25px;
}

.info__content--nobg {
  background-color: transparent;
  width: 100%;
  padding: 0;
  margin: 0;
}

</style>