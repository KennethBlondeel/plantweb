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
          this.projectData = response.data.data;
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
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  padding: 1em;
}

.p-all-projects__product-list{
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    width: 100%;
    padding:  0 4em ;
    overflow-y: scroll;
}

.p-all-projects__product-list__item{
      box-shadow: 0 5px 1.7px rgb(0 0 0 / 1%), 0 5.5px 2.4px rgb(0 0 0 / 2%),
  0 8.2px 3.6px rgb(0 0 0 / 3%), 0 1.8px 3.6px rgb(0 0 0 / 4%),
  0 1.2px 4.4px rgb(0 0 0 / 4%), 0 7px 8px rgb(0 0 0 / 6%);
  height: 250px;
  overflow: hidden;  
}

@media (max-width : 1350px){
  .p-all-projects{
    justify-content: unset;
    align-content: unset;
  }
}

@media (max-width: 700px){
  .p-all-projects{
    height: unset;
  }

  .p-all-projects__product-list{
    padding: 0 2em
  }

}

@media (max-width: 700px){
  .p-all-projects__product-list__item{
    height: unset;
  }

  .p-all-projects__product-list{
    display: grid;
    grid-template-columns: repeat(1, 1fr);
  }
}

</style>