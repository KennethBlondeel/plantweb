<template>
  <header class="c-header">
    <div class="c-header__logo-container">
      <img class="c-header__logo" src="http://134.122.95.37/assets/d849bae9-42f2-45b8-927c-00d54d69082c" alt="">
    </div>
    <div class="c-header__container">
      <nav class="c-header__nav">
        <nuxt-link
          v-for="navItem in navItems"
          :key="navItem.path"
          :class="{
            'c-header__nav__item': true,
            'c-header__nav__item--active': navItem.path === $route.path ,
          }"
          :to="navItem.path"
        >
          {{ navItem.label }}
        </nuxt-link>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: 'GlobalHeader',
  data() {
    return {
      navItems: [
        { path: '/', label: 'home' },
        { path: '/allprojects', label: 'projects' },
        { path: '/allplants', label: 'plants' },
        { path: '/contact', label: 'contact'}
      ],
    };
  },
};
</script>

<style lang="css">
.c-header {
    background-color: black;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    width: 40vw;
}

.c-header__container {
    display: flex;
    justify-content: space-between;
}

.c-header__logo {
  width: 35px;
  height: 35px;
  margin: 1em;
}

.c-header__nav {
  display: flex;
  justify-content: flex-end;
}

.c-header__nav__item {
  padding: 0 1em;
  text-decoration: none;
  color: white;
  
}

.c-header__nav__item--active {
    color: rgb(146, 175, 146);
}

.c-header__logo{
  height: 100%;
  width: 100%;
}

.c-header__logo-container{
  height: 120px;
  margin: 3em;
}

</style>