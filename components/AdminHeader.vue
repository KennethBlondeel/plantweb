<template>
  <header class="c-login">
    <div class="c-login__container">
      <div v-if="isAdmin">
        <nuxt-link class="c-login__link" to="/admin/user-requests">
          verzoeken
        </nuxt-link>
      </div>
      <div v-if="isLoggedIn">
        <a v-if="isLoggedIn" class="c-login__link" @click="logout"> Logout </a>
      </div>
      <div v-else>
        <nuxt-link class="c-login__link" to="/login"> login </nuxt-link>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'AccountHeader',
  data() {
    return {};
  },
  computed: {
    isLoggedIn() {
      return this.$store.getters['auth/isLoggedIn'];
    },
    isAdmin() {
      return this.$store.getters['auth/isAdmin'];
    },
    userName() {
      if (this.$store.getters['auth/getUser'] !== null) {
        return this.$store.getters['auth/getUser'].first_name;
      } else {
        return null;
      }
    },
  },
  methods: {
    logout() {
      this.$store.dispatch('auth/logout');
      this.$router.push('/login');
    },
  },
};
</script>

<style lang="css">
.c-login__container {
  width: 100%;
  height: 5vh;
  background-color: black;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  color: white;
  padding-right: 1em;
}
.c-login__link {
  color: white;
  text-decoration: none;
  margin: 0em 0.5em;
}
@media (max-width: 1350px) {
  .c-login__container {
    padding: 0 4em 0 0;
    height: 3vh;
    background-color: rgb(31, 31, 31);
  }
  .c-login__link {
    margin: 0em 1em;
  }
}
</style>
