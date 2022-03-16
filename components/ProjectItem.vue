<template>
  <article class="c-project-item">
    <div class="c-project-item__image-container">
      <img
        class="c-project-item__image"
        :src="src + project.images[0].directus_files_id"
        alt=""
      />
    </div>
    <div class="c-project-item__info">
      <div>
        <NuxtLink :to="`/project/${project.id}`">
          <h2 class="c-project-item__title">
            {{ project.bedrijf }}
          </h2>
        </NuxtLink>
      </div>

      <div class="c-project-item__content">
        <p>{{ project.text_content }}</p>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  name: 'ProjectItem',
  props: {
    project: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      src: 'http://134.122.95.37/assets/',
    };
  },
  methods: {},
};
</script>

<style lang="css">
.c-project-item {
  display: flex;
  background-color: rgb(235, 235, 235);
  color: black;
  border-radius: 15px;
  height: auto;
  margin: 0.5em;
}
.c-project-item__title {
  color: black;
  text-decoration: underline green;
}
.c-project-item__info {
  margin: 1em;
  overflow: hidden;
}
.c-project-item__image {
  min-height: 100%;
  max-height: 120%;
}
.c-project-item__image-container {
  overflow: hidden;
  min-width: 300px;
  max-width: 300px;
  max-height: 250px;
  border-radius: 15px 0 0 15px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.c-project-item__year {
  display: none;
}
@media (max-width: 700px) {
  .c-project-item__content {
    display: none;
  }
  .c-project-item__year {
    display: unset;
  }
  .c-project-item {
    flex-direction: row;
  }
  .c-project-item {
    flex-direction: column;
    height: unset;
  }
  .c-project-item__image-container {
    max-height: 250px;
    width: 100%;
    max-width: unset;
    min-width: unset;
    display: flex;
    justify-content: flex-start;
    align-content: flex-start;
  }
  .c-project-item__image {
    width: 100%;
    min-height: unset;
    max-height: unset;
  }
}
</style>
