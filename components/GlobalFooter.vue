<template>
  <div class="c-footer">
    <div class="c-footer__container">
        <p class="c-footer__item">Kenneth Blondeel</p> <span class="c-footer__space">•</span>
        <p class="c-footer__item">0471 38 39 36</p> <span class="c-footer__space">•</span>
        <p class="c-footer__item">kennethblondeel@hotmail.be</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GlobalFooter',
  data() {
    return {
    };
  },
};
</script>

<style lang="css">
.c-footer {
  background-color: black;
}

.c-footer__container {
    display: flex;
    justify-content: center;
}

.c-footer__logo {
  width: 35px;
  height: 35px;
  margin: 1em;
}

.c-footer__nav {
  display: flex;
  justify-content: flex-end;
}

.c-footer__item{
  padding: 1em;
  text-decoration: none;
  color: white;
}

.c-footer__space{
    color: white;
    padding: 1em;
}

</style>