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

<style>
.p-all-plants{
  width: 100vw;
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.p-all-plants__title{
  width: 100vw;
}
.p-all-plants__product-list{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    width: 70vw;
}
</style>