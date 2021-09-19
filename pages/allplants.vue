<template>
  <main class="p-all-plants">
    <h1 class="p-all-plants__title">alle planten</h1>
    <div class="p-all-plants__product-list">
      <PlantItem
        v-for="plant in plantData"
        :key="plant.id"
        class="p-all-plants__product-list__item"
        :plant="plant"
      />
    </div>
  </main>
</template>

<script>
import PlantItem from '~/components/PlantItem';
export default {
  name: 'AllPlantsPage',
  components: { PlantItem },
  data() {
    return {
      plantData: {},
      src: 'http://157.230.126.154/assets/',
    };
  },
  fetch() {
    return this.fetchplants();
  },
  created(){
      this.fetchplants()
  },
  methods: {
    fetchplants() {
      this.$axios('items/plants', {
        method: 'GET',
        headers: {},
        params: {
          fields: '*,images.*',
          filter:{ status: { _eq: "published" } },
        },
      })
        .then((response) => {
          console.log(response);
          this.plantData = response.data.data;
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>

<style lang="css">
.p-all-plants{
  width: 100%;
  height: 100vh;
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 1em;  
}
.p-all-plants__title{
  width: 100%;
}
.p-all-plants__product-list{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    width: 100%;
    padding:  0 4em ;
    overflow-y: scroll;
}

.p-all-plants__product-list__item{
      box-shadow: 0 5px 1.7px rgb(0 0 0 / 1%), 0 5.5px 2.4px rgb(0 0 0 / 2%),
  0 8.2px 3.6px rgb(0 0 0 / 3%), 0 1.8px 3.6px rgb(0 0 0 / 4%),
  0 1.2px 4.4px rgb(0 0 0 / 4%), 0 7px 8px rgb(0 0 0 / 6%);
    }
</style>