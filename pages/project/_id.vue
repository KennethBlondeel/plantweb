<template>
  <main class="p-project-page">
    <div class="p-project-page__container">
      <div class="p-project-page__info-container">
        <div class="p-project-page__hooper">
          <hooper>
            <slide v-if="images.length >= 1">
              <div class="p-project-page__image-container">
                <img
                  class="p-project-page__image"
                  :src="src + images[0]"
                  alt=""
                />
              </div>
            </slide>
            <slide v-if="images.length >= 2">
              <div class="p-project-page__image-container">
                <img
                  class="p-project-page__image"
                  :src="src + images[1]"
                  alt=""
                />
              </div>
            </slide>
            <slide v-if="images.length >= 3">
              <div class="p-project-page__image-container">
                <img
                  class="p-project-page__image"
                  :src="src + images[2]"
                  alt=""
                />
              </div>
            </slide>
            <slide v-if="images.length >= 4">
              <div class="p-project-page__image-container">
                <img
                  class="p-project-page__image"
                  :src="src + images[3]"
                  alt=""
                />
              </div>
            </slide>
            <slide v-if="images.length >= 5">
              <div class="p-project-page__image-container">
                <img
                  class="p-project-page__image"
                  :src="src + images[4]"
                  alt=""
                />
              </div>
            </slide>
            <hooper-pagination slot="hooper-addons"></hooper-pagination>
          </hooper>
        </div>
        <div class="p-project-page__info">
          <h1>{{ bedrijf }}</h1>
          <h3>{{ year }}</h3>

          <p class="p-project-page__text">{{ text_content }}</p>
          <p class="p-project-page__text">{{ text_content_2 }}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import { Hooper, Slide, Pagination as HooperPagination } from 'Hooper';
export default {
  name: 'ProjectIdPage',
  components: { Slide, Hooper, HooperPagination },
  data() {
    return {
      src: 'http://134.122.95.37/assets/',
      projectData: null,
      bedrijf: '',
      year: '',
      text_content: '',
      text_content_2: '',
      link: '',
      images: [],
    };
  },
  created() {
    this.fetchProject();
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
          this.projectData = data.data.data;
          this.bedrijf = this.projectData.bedrijf;
          this.year = this.projectData.year;
          this.text_content = this.projectData.text_content;
          this.text_content_2 = this.projectData.text_content_2;
          this.link = this.projectData.link;
          for (let i = 0; i < this.projectData.images.length; i++) {
            this.images.push(this.projectData.images[i].directus_files_id);
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
.p-project-page {
  margin: 4em 3em;
}
.p-project-page__hooper {
  min-width: 400px;
  max-width: 400px;
  overflow: hidden;
  margin-right: 3em;
  position: relative;
  float: left;
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
  width: 400px;
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
.hooper {
  width: 400px;
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
.p-project-page__container {
  display: flex;
  flex-direction: row;
}
.p-project-page__image {
  min-height: 400px;
  min-width: 400px;
  object-fit: cover;
  overflow: hidden;
}
.p-project-page__image-container {
  height: 400px;
  width: 400px;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 5px;
}
.p-project-page__text {
  margin-top: 1.5em;
}
.hooper-indicators li .is-active {
  border: 1px solid rgba(0, 0, 0, 0.281);
}
::marker {
  display: none;
  content: '';
}
@media (max-width: 1000px) {
  .p-project-page__container {
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .p-project-page__hooper {
    margin-right: 2em;
  }
}
@media (max-width: 700px) {
  .p-project-page__info-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .hooper-track {
    width: 300px;
  }
  .hooper-slide {
    width: 300px !important;
    height: 300px;
  }
  .p-project-page__image {
    min-width: 300px;
    min-height: 300px;
  }
  .p-project-page__image-container {
    width: 300px;
    height: 300px;
  }
  .p-project-page__hooper {
    max-width: 300px;
    min-width: 300px;
  }
  .hooper {
    width: 300px;
  }
  .p-project-page__hooper {
    float: initial;
    position: initial;
    margin-right: 0em !important;
  }
  .p-project-page {
    margin: 2em 1em;
  }
}
</style>
