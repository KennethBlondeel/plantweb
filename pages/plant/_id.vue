<template>
  <main class="p-plant-page">
    <div class="p-plant-page__container">
      <Carousel>
        <Slide>
          <img  class="p-plant-page__image" :src="src +images" alt="" />
        </Slide>
      </Carousel>
      <div class="p-plant-page__info-container">
        <div class="p-plant-page__info">
          <h1>{{ plantData.name }}</h1>
          <h3>{{ plantData.latin }}</h3>
          <p>{{ plantData.light }}</p>
          <p>{{ plantData.water }}</p>
        </div>
      </div>
    </div>
    <div class="p-plant-page__care">
      <h3>omschrijving</h3>
      <p>{{ plantData.plant_description }}</p>
    </div>

  </main>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel';

export default {
  name: 'PlantIdPage',
  components: {
    Carousel,
    Slide
  },
  data() {
    return {
      src: 'http://134.122.95.37/assets/',
      plantData: [],
      images: [],
    };
  },
  fetch() {
    return this.fetchPlant();
  },
created(){
    this.fetchPlant()
},
  methods: {
    fetchPlant() {
      this.$axios('items/plants/' + this.$route.params.id, {
        method: 'GET',
        headers: {},
        params: {
          fields: '*.*',
        },
      })
        .then((data) => {
          this.plantData = data.data.data;

          for(let i = 0; i< this.plantData.images.length ; i++){
            console.log(i)
            this.images.push( this.plantData.images[i].directus_files_id);
          }
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>

<style>
.p-plant-page{
  margin: 4em 3em;
}

.p-plant-page__container{
    display: flex;
  flex-direction: row;
}

.p-plant-page__image{
  height: 450px;
  margin: 0 2em 2em 0;
}
</style>