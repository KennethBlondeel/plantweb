<template>
  <section >
    <div class="p-home--background">
      <div class="p-home__card">
        <div class="p-home__card-image-container">
          <img class="p-home__card-image" src="http://134.122.95.37/assets/16f4484e-b2d2-4bca-be92-9ebce9a43a07" alt="Kenneth Blondeel standing on a road">
        </div>
        <div class="p-home__card-content">
          <h1 class="p-home__card-content-title">Kenneth Blondeel</h1>
          <p class="p-home__card-content-function">front end developer</p>
          <p class="p-home__card-content-me">Hello, i'm Kenneth Blondeel a freelance front-end developer and graphic designer from Belgium 🇧🇪. I have a modern en innovating look at my design's and I am always open for suggestions on upgrading it. In the project page I made an overview of al the projects i have worked on. If i can help you with you're projects feel free to contact me and maybe we can work together.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {}
</script>

<style lang="scss">
.p-home{

  &__hero{
  display: flex;
  align-items: center;
  justify-content: center;
  height: 200px;
  }

  &--background{
  height: 100vh;
  background-image: url("http://134.122.95.37/assets/65be13a0-b803-4ce0-87bc-fd3944529fdd");
  background-color: rgba(0, 0, 0, 0.384);
  background-size: cover;

  display: flex;
  justify-content: center;
  align-items: center;
  }

  &__card{
  background-color: white;
  width: 55vw;
  height: 60vh;
  display: flex;
  border-radius: 15px;
  overflow: hidden;

    &-image-container{
    height: 100%;
    width: 80vw;
    overflow: hidden;
    display: flex;
    justify-content: center;
    }

    &-image{
    height: 100%;
    border-radius: 15px 0 0 15px;
    }

    &-content{
    padding: 1.5em;

      &-title{
      color: green;
      margin-bottom: 0.5em;
      font-weight: bolder;
      font-size: 2em;
      }

      &-function{
      margin-bottom: 1em;
      font-weight: bold;
      }

      &-me{
      margin-bottom: 0.5em;
      }
    }
  }
}


@media (max-width:1300px){
  .p-home__card{
    width: 70vw;
  }
  .p-home__card-image-container{
    width: 150%;

  }
}

@media (max-width: 700px){
  .p-home__card-image-container{
    display: none;
  }
}
</style>
