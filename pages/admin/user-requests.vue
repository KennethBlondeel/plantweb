<template>
  <section class="p-request">
    <div class="p-request-items__list">
      <UserRequestItem
        v-for="request in requestData.data"
        :key="request.id"
        class="p-request-items"
        :request="request"
        @done-request="doneRequest($event)"
      />
    </div>
  </section>
</template>

<script>
export default {
  name: 'GetAllRequestsPage',
  layout: 'admin',
  data() {
    return {
      requestData: {},
    };
  },
  created() {
    this.isAdmin();
  },
  methods: {
          isAdmin() {
              if(this.$store.getters['auth/isAdmin'] === true){
                  console.log('welcome admin')
                  this.fetchRequest()
              }else{
                  console.log('bye please login first')
                  this.$router.push('/login');
              }
    },

    fetchRequest() {
      this.$axios('items/user_requests', {
        method: 'GET',
        headers: {},
        params: {
          fields: '*.*',
          sort: '-date_created',
          filter: { done: { _neq: true } },
        },
      })
        .then((response) => {
          console.log(response);
          this.requestData = response.data;
        })
        .catch((err) => {
          console.error(err);
        });
    },
    doneRequest(request) {
      this.$axios(`items/user_requests/${request.id}`, {
        method: 'PATCH',
        headers: {},
        data: {
          done: true,
        },
      })
        .then(() => {
          return this.fetchRequest();
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>

<style lang="css">
.p-request {
  height: 90vh;

}

.p-request-items {
    width: 50vw;
    padding: 1.5em;
    margin: 1em;
    background-color: rgb(194, 209, 194);
    color: black;
    border-radius: 15px;
}


.p-request-items__list {
      display: flex;
      flex-direction: column;
      align-items: center;
      overflow-y: scroll;
      padding: 0 4em;
      height: 90vh;
}
</style>
