<template>
  <header>
    <nuxt-link to="/"><h1>Pixel Plus</h1></nuxt-link>
    <Navbar />
    <img :src="src" />
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {},
  data() {
    return {
      src:
        'https://media-exp1.licdn.com/dms/image/C560BAQHWR1ouQ__obA/company-logo_200_200/0/1519890096467?e=1621468800&v=beta&t=Y-XJLKl6KN-e-hInGypeVkWW9-98tsEItCJSGrB7O1w',
    }
  },
}
</script>

<style lang="scss">
header {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  a {
    text-decoration: none;
    color: #000;

    h1 {
      font-size: 22px;
    }
  }

  img {
    width: 50px;
    border-radius: 50%;
  }
}
</style>
