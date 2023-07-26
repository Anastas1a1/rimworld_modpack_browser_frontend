<template>
  <nav>
    <router-link to="/">Домашняя страница</router-link> |
    <router-link to="/mods">Мои сборки</router-link>
  </nav>
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: aliceblue;
}

nav {
  padding: 30px;
  background-color: #3E5575;
}

nav a {
  font-weight: bold;
  color: aliceblue;
}

nav a.router-link-exact-active {
  color: #6C80EF;
}
</style>
