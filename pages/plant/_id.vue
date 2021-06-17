<template>
  <main class="p-plant-page">
    <div class="p-plant-page__container">
              <img class="p-plant-page__image" :src="src +images" alt="" />
      <div class="p-plant-page__info-container">
        <div class="p-plant-page__info">
          <h1>{{ name }}</h1>
          <h3>{{ latin }}</h3>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'PlantPage',
  data() {
    return {
      src: 'http://134.122.95.37/assets/',
      plantData: null,
      name: '',
      latin: '',
      images: '',
    };
  },
  fetch() {
    console.log(this.$route.params.id);
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
          console.log(data);
          this.plantData = data.data.data;
          this.name = this.plantData.name;
          this.latin = this.plantData.latin;
          this.images = this.plantData.images[0].directus_files_id;
          console.log(this.images)
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>