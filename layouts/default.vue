<template>
  <div class="web-body">
    <GlobalHeader />
    <div class="main-body">
      <Nuxt />
      <Notify />
    </div>
  </div>
</template>

<script>
import GlobalHeader from '~/components/GlobalHeader.vue';
import Notify from '~/components/Notify';

export default {
  name: 'GlobalLayout',
  components: { GlobalHeader, Notify },
};
</script>


<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}



.web-body{
  display: flex;
}

.main-body{
  height: 100vh;
  width: 100%;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

::-webkit-scrollbar {
  width: 0px;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}

@media (max-width:1350px){
  .web-body{
    display: flex;
    flex-direction: column;
  }
}




</style>
