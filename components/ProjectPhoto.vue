<template>
  <article class="c-plant-photo">
      <img class="c-plant-photo__image" :src="src + plant.images[0].directus_files_id" alt="" />
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


</style>