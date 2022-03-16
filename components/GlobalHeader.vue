<template>
  <header class="c-header">
    <div class="c-header__logo-container">
      <img
        class="c-header__logo"
        src="http://134.122.95.37/assets/d849bae9-42f2-45b8-927c-00d54d69082c"
        alt="logo of the website"
      />
    </div>
    <div class="c-header__container">
      <nav class="c-header__nav">
        <nuxt-link
          v-for="navItem in navItems"
          :key="navItem.path"
          :class="{
            'c-header__nav__item': true,
            'c-header__nav__item--active': navItem.path === $route.path,
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
        { path: '/', label: 'HOME' },
        { path: '/allprojects', label: 'PROJECTS' },
        { path: '/allplants', label: 'PLANTS' },
        { path: '/contact', label: 'CONTACT' },
      ],
      adminItems: [{ path: '/login', label: 'login' }],
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
  font-size: 1.2em;
}
.c-header__nav__item:hover {
  color: rgb(197, 218, 197);
}
.c-header__nav__item--active {
  color: rgb(146, 175, 146);
}
.c-header__admin__item--hide {
  color: red;
}
.c-header__logo {
  height: 100%;
  width: 100%;
}
.c-header__logo-container {
  height: 120px;
  margin: 3em;
}
@media (max-width: 1350px) {
  .c-header {
    width: 100vw;
    height: 100%;
    flex-direction: row;
    align-content: center;
    justify-content: space-between;
    padding: 0 4em;
  }
  .c-header__logo {
    height: 40px;
    width: 40px;
    margin: 0;
  }
  .c-header__logo-container {
    height: 40px;
    margin: 0;
    display: flex;
    align-content: center;
    justify-content: center;
  }
}
@media (max-width: 550px) {
  .c-header__nav {
    flex-direction: column;
    align-items: center;
    margin-bottom: 0.5em;
  }
  .c-header__nav__item {
    margin: 0.1em 0;
  }
  .c-header {
    flex-direction: column;
  }
}
</style>
