<template>
  <section>
    <div class="p-home--background">
      <div class="p-home__card">
        <div class="p-home__card-image-container">
          <img
            class="p-home__card-image"
            src="http://134.122.95.37/assets/16f4484e-b2d2-4bca-be92-9ebce9a43a07"
            alt=""
          />
        </div>
        <div class="p-home__card-content">
          <h1 class="p-home__card-content-title">Kenneth Blondeel</h1>
          <p class="p-home__card-content-function">front end developer</p>
          <p class="p-home__card-content-me">
            Hello, i'm Kenneth Blondeel a freelance front-end developer and
            graphic designer from Belgium 🇧🇪. I have a modern en innovating look
            at my design's and i am always open for suggestions on upgrading it
            .
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {};
</script>

<style>
.p-home__hero {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 200px;
}

.p-home--background {
  height: 100vh;
  background-image: url('http://134.122.95.37/assets/65be13a0-b803-4ce0-87bc-fd3944529fdd');
  background-color: rgba(0, 0, 0, 0.384);
  background-size: cover;

  display: flex;
  justify-content: center;
  align-items: center;
}

.p-home__card {
  background-color: white;
  width: 900px;
  height: 500px;
  display: flex;
  border-radius: 15px;
}

.p-home__card-image-container {
  height: 500px;
}

.p-home__card-image {
  height: 500px;
  border-radius: 15px 0 0 15px;
}

.p-home__card-content {
  padding: 1.5em;
}

.p-home__card-content-title {
  color: green;
  margin-bottom: 0.5em;
  font-weight: bolder;
}

.p-home__card-content-function {
  margin-bottom: 1em;
  font-weight: bold;
}

.p-home__card-content-me {
  margin-bottom: 0.5em;
}
</style>
