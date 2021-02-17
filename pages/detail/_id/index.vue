<template>
  <div class="detail-person">
    <img :src="person.avatar" :alt="person.first_name" />
    <h1>{{ person.first_name }} {{ person.last_name }}</h1>
    <p>{{ person.email }}</p>
    <nuxt-link to="/"><span>Geri</span></nuxt-link>
  </div>
</template>

<script>
export default {
  name: 'Detail',
  data() {
    return {
      person: [],
    }
  },
  async fetch() {
    const user = await fetch(
      `https://reqres.in/api/users/${this.$route.params.id}`
    ).then((res) => res.json())

    this.person = user.data
  },
}
</script>

<style lang="scss">
.detail-person {
  width: 100%;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  margin-top: 100px;

  img {
    width: 250px;
    height: 250px;
    border-radius: 50%;
    margin-bottom: 30px;
  }

  p {
    font-size: 24px;
    margin: 30px 0;
  }

  span {
    text-decoration: none;
    color: #000;
  }
}
</style>
