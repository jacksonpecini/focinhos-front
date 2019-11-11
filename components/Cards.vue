<template>
  <div class="cards">
      <div class="cards__content">
          <slot/>
      </div>
  </div>
</template>

<script>
export default {

};
</script>

<style>

.cards {
  background-color: var(--color-primary);
  max-width: 800px;
  padding: 20px;
  display: flex;
  border-radius: 25px;
  position: center;
}

.cards__content {
  width: 100%;
  padding: 20px;
  font-size: 20px;
  color: #fff;
  text-align: center;
  border-radius: 25px;
}

</style>