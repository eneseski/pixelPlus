<template>
  <nav>
    <nuxt-link to="/create">Aday Oluştur</nuxt-link>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
}
</script>

<style lang="scss">
nav {
  a {
    text-decoration: underline;
    font-size: 16px;
    font-weight: bold;
    color: purple;
  }
}
</style>
