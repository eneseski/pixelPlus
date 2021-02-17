<template>
  <div>
    <nuxt-link :to="`/detail/${person.id}`">
      <div class="person-card">
        <img :src="person.avatar" />
        <h6>{{ person.first_name }} {{ person.last_name }}</h6>
      </div>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    person: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style lang="scss">
.person-card {
  background-color: lightgray;
  padding: 20px;
  margin-bottom: 10px;
  border: 2px solid grey;
  border-radius: 4px;
  transition: all 0.2s ease-out;
  cursor: pointer;
  text-align: center;
  margin: 5px 10px;

  &:hover {
    box-shadow: 5px 5px 5px rgba(68, 68, 68, 0.6);
    transition: all 0.2s ease-out;
  }

  img {
    width: 200px;
    height: 200px;
    border-radius: 50%;
  }

  h6 {
    margin-top: 15px;
    font-size: 18px;
  }
}
</style>
