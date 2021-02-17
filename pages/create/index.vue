<template>
  <div class="create-person">
    <form @submit.prevent="onSubmit">
      <div>
        <label for="fname">Name:</label>
        <input
          id="fname"
          v-model="form.name"
          v-validate="'required'"
          type="text"
          name="fname"
        />
      </div>
      <div>
        <label for="lname">Job:</label>
        <input
          v-model="form.job"
          v-validate="'required'"
          d="lname"
          type="text"
          name="lname"
        />
      </div>
      <input type="submit" value="Oluştur" />
    </form>
    <nuxt-link to="/">Geri</nuxt-link>
    <transition name="fade">
      <div v-if="person.name" class="saved-person">
        <p>Tebrikler Kayıt Oluşturuldu</p>
        <p>Id: {{ person.id }}</p>
        <p>Name: {{ person.name }}</p>
        <p>Job: {{ person.job }}</p>
        <p>Create Date: {{ person.createdAt }}</p>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'Create',
  data() {
    return {
      person: [],
      form: {
        name: '',
        job: '',
      },
    }
  },

  methods: {
    async onSubmit() {
      const users = await this.$axios.$post(
        'https://reqres.in/api/users',
        this.form
      )

      this.person = users
    },
  },
}
</script>

<style lang="scss">
.create-person {
  display: flex;
  flex-direction: column;
  align-items: center;

  form {
    margin: 100px 0;
    display: flex;
    flex-direction: column;
    align-items: flex-end;

    label {
      font-size: 22px;
    }

    input {
      height: 40px;
      font-size: 22px;
      margin: 5px 0;
    }
  }

  .saved-person {
    padding: 20px;
    p {
      &:first-child {
        font-size: 28px;
        margin-bottom: 15px;
      }

      font-size: 22px;
    }
  }
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 1s;
  }
  .fade-enter,
  .fade-leave-to {
    opacity: 0;
  }
}
</style>
