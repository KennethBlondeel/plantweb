<template>
  <article class="c-plant-item">
    <div class="c-plant-item__image-container">
      <img class="c-plant-item__image" :src="src + plant.images[0].directus_files_id" alt="" />
    </div>
    <div class="c-plant-item__info">
      <div>
        <NuxtLink :to="`/plant/${plant.id}`">
          <h2 class="c-plant-item__title">
            {{ plant.name }}
          </h2>
        </NuxtLink>
      </div>

      <div class="c-plant-item__content">
        <p>Price: € {{ plant.latin }}</p>
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
  background-color: black;
  border-radius: 15px;
  height: auto;
  margin: 0.5em;
}
.c-plant-item__image {
    overflow: hidden;
    max-height: 400px;
}
.c-plant-item__info {
    margin: 1em;
}
.c-plant-item__image-container{
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
}
.c-plant-item__image{
    overflow: hidden;
    width: 300px;
}
</style>