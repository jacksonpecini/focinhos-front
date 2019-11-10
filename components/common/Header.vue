<template>
  <header class="header">
    <div class="container header__container">
      <div class="brand">
        <img src="~/assets/logo.png" class="brand--image" alt="Logo" />
        <p class="brand--text">Focinhos Anônimos</p>
      </div>
      <nav class="header__nav">
        <a href="/about" class="header__item">About</a>
        <a href="/faq" class="header__item">FAQ</a>
        <a href="/ajuda" class="header__item">Ajuda</a>
      </nav>
      <a href="/login" class="header__item">Login</a>
    </div>
  </header>
</template>

<script>
export default {};
</script>

<style>
.header {
  background-color: var(--color-primary);
}

.header__container {
  display: flex;
  padding: 20px;
  align-items: center;
  justify-content: space-between;
}

.brand {
  display: flex;
  align-items: center;
}

.brand--text {
  color: var(--color-highlight);
  font-weight: bold;
  font-size: 30px;
}

.brand--image {
  margin-right: 10px;
}
</style>