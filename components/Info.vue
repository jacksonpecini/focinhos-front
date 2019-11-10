<template>
  <div class="info">
      <div class="info__content">
          <slot/>
      </div>
  </div>
</template>

<script>
export default {

};
</script>

<style>

.info {
  background-color: var(--color-primary);
  width: 500px;
  padding: 20px;
  display: flex;
  border-radius: 25px;
}

.info__content {
  background-color: var(--color-grey);
  width: 100%;
  padding: 20px;
  font-size: 20px;
  color: #fff;
  text-align: center;
  border-radius: 25px;
}

</style>