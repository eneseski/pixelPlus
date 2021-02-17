<template>
  <footer>
    <p>Tüm hakları saklıdır</p>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
}
</script>

<style lang="scss">
footer {
  width: 100%;
  text-align: center;
  position: fixed;
  bottom: 30px;

  @media (max-width: 768px) {
    position: initial;
  }
}
</style>
