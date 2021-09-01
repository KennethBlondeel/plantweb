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
  },
  watch: {
    isLoggedIn(newVal) {
        console.log(newVal)
    },
  },
  methods: {
    login() {
      this.$store.dispatch('auth/login', this.loginBody);
      this.$root.$emit('notify', 'Welkom user!');
      if(this.$store.getters['auth/isAdmin'] === true){
          this.$router.push('/admin/user-requests');
      }else{
      this.$root.$emit('notify', "user can't do anything extra dan public users");
      }
      this.email = '';
      this.password = '';
    },
  },
};
</script>

<style>
.p-login{
  height: 95vh;
}

.p-login__background{
  height: 95vh;
  background-image: url("http://134.122.95.37/assets/6ce933ee-d233-48eb-97c6-1172f522e3d9");
  background-color: rgba(0, 0, 0, 0.384);
  background-size: cover;

}

.p-login__container{
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  width: 100%;
}

.p-login__overlay{
  background-color: white;
  padding: 3em;
  border-radius: 10px;
  width: 500px;
  height: 350px;
}
</style>