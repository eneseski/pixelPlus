<template>
  <div class="person-cards">
    <div class="person-cards__card">
      <Card
        v-for="(person, index) in persons"
        :key="index"
        :person="person"
      ></Card>
    </div>
    <div class="pagination">
      <Pagination
        v-for="(page, index) in totalPages"
        :key="`key-${index}`"
        :page="page"
        :current-page="currentPage"
        @setPage="setPage"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      persons: [],
      currentPage: 1,
      totalPages: null,
    }
  },
  async fetch() {
    const users = await fetch(
      `https://reqres.in/api/users?page=${this.currentPage}`
    ).then((res) => res.json())

    this.persons = users.data
    this.totalPages = users.total_pages
  },
  methods: {
    setPage(page) {
      this.currentPage = page
      this.$fetch()
    },
  },
}
</script>

<style lang="scss">
.person-cards {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;

  &__card {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    width: 50%;

    @media (max-width: 576px) {
      width: 100%;
      padding: 20px 20px;
    }

    a {
      text-decoration: none;
      color: purple;
    }
  }
}
</style>
