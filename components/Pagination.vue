n
<template>
  <div>
    <button
      :disabled="currentPage === page"
      class="pagination__btn"
      @click="setPage(page)"
    >
      {{ page }}
    </button>
  </div>
</template>

<script>
export default {
  name: 'Pagination',
  props: {
    page: {
      type: Number,
      required: true,
    },
    currentPage: {
      type: Number,
      required: true,
    },
  },
  methods: {
    setPage(page) {
      this.$emit('setPage', page)
      window.scrollTo({ top: 0, behavior: 'smooth' })
    },
  },
}
</script>

<style lang="scss">
.pagination {
  display: flex;
  justify-content: center;
  margin: 30px 0;

  &__btn {
    font-size: 22px;
    margin-right: 10px;
    cursor: pointer;
  }
}
</style>
