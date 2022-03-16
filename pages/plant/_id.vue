<template>
  <main class="p-plant-page">
    <div class="p-plant-page__container">
      <div class="p-plant-page__hooper">
        <hooper>
          <slide v-if="images.length >= 1">
            <div class="p-plant-page__image-container">
              <img class="p-plant-page__image" :src="src + images[0]" alt="" />
            </div>
          </slide>
          <slide v-if="images.length >= 2">
            <div class="p-plant-page__image-container">
              <img class="p-plant-page__image" :src="src + images[1]" alt="" />
            </div>
          </slide>
          <slide v-if="images.length >= 3">
            <div class="p-plant-page__image-container">
              <img class="p-plant-page__image" :src="src + images[2]" alt="" />
            </div>
          </slide>
          <slide v-if="images.length >= 4">
            <div class="p-plant-page__image-container">
              <img class="p-plant-page__image" :src="src + images[3]" alt="" />
            </div>
          </slide>
          <slide v-if="images.length >= 5">
            <div class="p-plant-page__image-container">
              <img class="p-plant-page__image" :src="src + images[4]" alt="" />
            </div>
          </slide>
          <hooper-pagination slot="hooper-addons"></hooper-pagination>
        </hooper>
      </div>
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
import { Hooper, Slide, Pagination as HooperPagination } from 'Hooper';
export default {
  name: 'PlantIdPage',
  components: { Slide, Hooper, HooperPagination },
  data() {
    return {
      src: 'http://134.122.95.37/assets/',
      plantData: [],
      images: [],
      imagesLenght: 0,
    };
  },
  created() {
    this.fetchPlant();
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

          for (let i = 0; i < this.plantData.images.length; i++) {
            this.images.push(this.plantData.images[i].directus_files_id);
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
.p-plant-page {
  margin: 4em 3em;
}
.p-plant-page__hooper {
  width: 400px;
  margin: 0 2em 2em 0;
  overflow: hidden;
}
.hooper-slide {
  width: 400px;
  height: 400px;
  display: table;
  overflow: hidden;
}
.hooper-track {
  padding: 0;
  display: flex;
  align-items: flex-start;
  width: 100%;
}
.hooper-sr-only {
  display: none;
}
.hooper-indicators {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0;
}
.hooper-indicator {
  height: 15px;
  width: 15px;
  border-radius: 30px;
  border: 1px solid rgb(194, 209, 194);
  background-color: rgb(194, 209, 194);
  padding: 0em;
  margin: 1em 0.2em 0;
}
.p-plant-page__container {
  display: flex;
  flex-direction: row;
}
.p-plant-page__image {
  min-height: 400px;
  min-width: 400px;
  object-fit: cover;
  overflow: hidden;
}
.p-plant-page__image-container {
  height: 400px;
  width: 400px;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 5px;
}
.hooper-indicators li .is-active {
  border: 1px solid rgba(0, 0, 0, 0.281);
}
::marker {
  display: none;
  content: '';
}
@media (max-width: 1000px) {
  .p-plant-page__container {
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .p-plant-page__hooper {
    margin: 0 0 2em 0;
  }
  .p-plant-page__info-container {
    width: 100%;
    padding-bottom: 1em;
  }
}
</style>
