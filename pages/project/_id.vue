<template>
  <main class="p-project-page">
    <div class="p-project-page__container">
      <div class="p-project-page__image-container">
              <img
               class="p-project-page__image" :src="src + images" alt="" />
      </div>
      <div class="p-project-page__info-container">
        <div class="p-project-page__info">
          <h1>{{ bedrijf }}</h1>
          <h3>{{ year }}</h3>
          <p>{{link}}</p>

          <p>{{text_content}}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>

export default {
  name: 'ProjectIdPage',
  components: { },
  data() {
    return {
      src: 'http://134.122.95.37/assets/',
      projectData: null,
      bedrijf: '',
      year: '',
      text_content: '',
      link: '',
      images: [],
    };
  },
  fetch() {
    console.log(this.$route.params.id);
    return this.fetchProject();
  },
created(){
    this.fetchProject()
},
  methods: {
    fetchProject() {
      this.$axios('items/projects/' + this.$route.params.id, {
        method: 'GET',
        headers: {},
        params: {
          fields: '*.*',
        },
      })
        .then((data) => {
          console.log(data);
          this.projectData = data.data.data;
          this.bedrijf = this.projectData.bedrijf;
          this.year = this.projectData.year;
          this.text_content = this.projectData.text_content;
          this.link = this.projectData.link;

         for (let i = 0; i < this.projectData.images.length; i++ ){
          this.images.push(this.projectData.images[i].directus_files_id);
          }
          console.log(this.images)
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>

<style>
.p-project-page{
  padding: 2em;
}

.p-project-page__container{
  display: flex;
}

.p-project-page__image-container{
  width: 50%;
}

.p-project-page__image{
  height: 300px;
}

.p-plant-page__info{
  color: black;
}
</style>