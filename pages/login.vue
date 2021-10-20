<template>
  <main class="p-login">
    <div class="p-login__background">
      <div class="p-login__container">
    <div class="p-login__overlay">
      <h1>Login</h1>
      <div class="p-login__content">
        <FormulateForm class="p-login__form" @submit="login">
          <FormulateInput
            v-model="email"
            name="email"
            type="email"
            label="email"
            validation-name="email"
            validation="required|email"
          />
          <FormulateInput
            v-model="password"
            name="password"
            type="password"
            label="Wachtwoord"
            validation-name="wachtwoord"
            validation="required"
          />
          <FormulateInput type="submit" label="Inloggen" />
        </FormulateForm>
      </div>
    </div>
    </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'LoginPage',
    layout: 'admin',
  data() {
    return {
      email: '',
      password: '',
    };
  },
  computed: {
    loginBody() {
      return { email: this.email, password: this.password };
    },
    isLoggedIn() {
      return this.$store.getters['auth/isLoggedIn'];
    },
    isAdmin(){
     return this.$store.getters['auth/isAdmin'];
    }
  },
  watch: {
    isAdmin(newVal) {
      if(newVal){
        this.$router.push('/admin/user-requests')
        this.$root.$emit('notify', 'Welkom user!');
      }
    },
  },
  methods: {
    login() {
      this.$store.dispatch('auth/login', this.loginBody);
      this.email='';
      this.password='';
    },
  },
};
</script>

<style lang="scss">
.p-login{
  height: 95vh;

  &__background{
  height: 95vh;
  background-image: url("http://134.122.95.37/assets/6ce933ee-d233-48eb-97c6-1172f522e3d9");
  background-color: rgba(0, 0, 0, 0.384);
  background-size: cover;
  }

  &__container{
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  width: 100%;
  }

  &__overlay{
  background-color: white;
  padding: 3em;
  border-radius: 10px;
  width: 500px;
  height: 350px;
  }
}

@media (max-width: 700px){
  .p-login__overlay{
    width: 250px;
  }
}
</style>