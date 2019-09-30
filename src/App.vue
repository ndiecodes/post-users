<template>
  <div id="app">
    <div id="nav">
      <h1 class="text-2xl text-indigo-600 font-extrabold logo-text p-5"> Users and Posts </h1>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.logo-text:hover {
  transform: skew(20deg);

}
</style>
