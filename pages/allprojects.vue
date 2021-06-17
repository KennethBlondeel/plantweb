<template>
  <main class="p-all-projects">
    <h1 class="p-all-projects__title">alle projecten</h1>

    <div class="p-all-projects__product-list">
      <ProjectItem
        v-for="project in projectData"
        :key="project.id"
        class="p-all-projects__product-list__item"
        :project="project"
      />
    </div>
  </main>
</template>

<script>
import ProjectItem from '~/components/ProjectItem';

export default {
  name: 'AllProjectsPage',
  components: { ProjectItem },
  data() {
    return {
      projectData: {},
      src: 'http://157.230.126.154/assets/',
    };
  },
  fetch() {
    return this.fetchProjects();
  },
  created(){
      this.fetchProjects()
  },
  methods: {
    fetchProjects() {
      this.$axios('items/projects', {
        method: 'GET',
        headers: {},
        params: {
          fields: '*,images.*',
          filter:{ status: { _eq: "published" } },
        },
      })
        .then((response) => {
          console.log(response);
          this.projectData = response.data.data;
          console.log(this.projectData)
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>

<style lang="css">
.p-all-projects{
  width: 100vw;
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.p-all-projects__title{
  width: 100vw;
}
.p-all-projects__product-list{
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    width: 70vw;
}

.p-all-projects__product-list__item{
      box-shadow: 0 5px 1.7px rgb(0 0 0 / 1%), 0 5.5px 2.4px rgb(0 0 0 / 2%),
  0 8.2px 3.6px rgb(0 0 0 / 3%), 0 1.8px 3.6px rgb(0 0 0 / 4%),
  0 1.2px 4.4px rgb(0 0 0 / 4%), 0 7px 8px rgb(0 0 0 / 6%);;
    }

</style>