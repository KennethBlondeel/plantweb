<template>
  <article class="c-plant-item">
    <div class="c-plant-item__image-container">
      <img class="c-plant-item__image" :src="src + plant.images[0].directus_files_id" alt="" />
    </div>
    <div class="c-plant-item__info">
      <div>
        <NuxtLink :to="`/plant/${plant.id}`">
          <h2 class="c-plant-item__title">
            {{ plant.latin }}
          </h2>
        </NuxtLink>
      </div>

      <div class="c-plant-item__content">
        <p>{{ plant.name }}</p>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  name: 'PlantItem',
  props: {
    plant: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      src: 'http://134.122.95.37/assets/',
    };
  },
  methods: {
  },
};
</script>

<style lang="css">
.c-plant-item {
  background-color: rgb(235, 235, 235);
  color: black;
  border-radius: 15px;
  height: auto;
  margin: 0.5em;
}

.c-plant-item__title{
    text-decoration: none;
    color: black;
  }



.c-plant-item__info {
      margin: 1em;
  }

.c-plant-item__image{
    overflow: hidden;
    width: 100%;
}

.c-plant-item__image-container{
      border-radius: 15px 15px 0 0;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 250px;
    }

</style>