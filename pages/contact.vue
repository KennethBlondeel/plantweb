<template>
  <main>
    <section class="contact">
      <div class="contact-image"></div>
      <section class="contact-data__container">
        <p class="contact-data">
        </p>
      </section>
      <section class="contact-form">
        <h1>Contact</h1>
        <FormulateForm
          v-model="contactData"
          class="contact-form__inputs"
          @submit="postRequest"
        >
          <FormulateInput name="first_name" type="text" label="voornaam:" />
          <FormulateInput name="last_name" type="text" label="achternaam:" />
          <FormulateInput name="email" type="email" label="email" />
          <FormulateInput
            name="tel_number"
            type="number"
            label="telefoon nummer"
          />
          <FormulateInput
            name="text_content"
            type="textarea"
            label="Waarmee kunnen wij u helpen?"
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

<style lang="css">

</style>