<template>
  <main>
    <section class="contact">
      <div class="contact-image"></div>
      <section class="contact-data__container">
        <p class="contact-data">
          In the contact form below you can reach out to me if you would like me
          to work on a project that involves graphic design or frondend
          development. I try to answer every request within a week.
        </p>
      </section>
      <section class="contact-form">
        <FormulateForm
          v-model="contactData"
          class="contact-form__inputs"
          @submit="postRequest"
        >
          <FormulateInput
            class="input"
            name="first_name"
            type="text"
            label="voornaam:"
            validation="required"
            validation-name="voornaam"
          />
          <FormulateInput
            name="last_name"
            type="text"
            label="achternaam:"
            validation="required"
            validation-name="achternaam"
          />
          <FormulateInput
            name="email"
            type="email"
            label="email"
            validation="required|email"
          />
          <FormulateInput
            name="tel_number"
            type="tel"
            label="telefoon nummer"
            validation="required"
            validation-name="telefoon nummer"
          />
          <FormulateInput
            name="text_content"
            type="textarea"
            label="Waarmee kunnen wij u helpen?"
            validation="required"
            validation-name="dit veld"
          />
          <FormulateInput type="submit" label="verstuur" />
        </FormulateForm>
      </section>
    </section>
  </main>
</template>

<script>
export default {
  name: 'ContactPage',
  layout: 'admin',
  data() {
    return {
      contactData: {
        first_name: '',
        last_name: '',
        email: '',
        tel_number: '',
        text_content: '',
      },
    };
  },
  methods: {
    postRequest(data) {
      return this.$axios('/items/user_requests', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        data,
      })
        .then((response) => {
          console.log(response);
          this.$root.$emit('notify', 'Je verzoek is verstuurd!');
          return response.data.data;
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>

<style>
.contact-form {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 70vh;
}
.contact-form__inputs {
  display: flex;
  flex-direction: column;
  margin: 1em;
  justify-content: space-between;
  height: 100%;
  width: 80%;
  padding: 3em;
}
.contact {
  height: 95vh;
}
.contact-data__container {
  background-color: rgb(194, 209, 194);
  height: 20vh;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.contact-data {
  width: 70%;
  text-align: center;
}
@media (max-width: 700px) {
  .contact-data__container {
    height: unset;
    padding: 1em 0;
  }
  .contact-form {
    height: unset;
  }
  .contact-form__inputs {
    margin: 2em 3em;
    padding: 0;
  }
}
@media (max-width: 1350px) {
  .contact-form__inputs {
    justify-content: initial;
  }
}
</style>
