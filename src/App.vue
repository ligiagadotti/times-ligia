<script setup>
import HeaderComp from "./components/template/HeaderComp.vue";
import RodapeCom from "./components/template/RodapeCom.vue";
</script>

<template>
  <HeaderComp />
  <main>
    <RouterView />
  </main>
  <RodapeCom />
</template>

<style>
@import "@/assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  height: 95vh;

  font-weight: normal;
}
a {
  color: inherit;
  text-decoration: none;
}
.router-link-active {
  font-weight: bold;
}
footer {
  height: 10%;
  background-color: rgb(82, 65, 94);
  color: rgb(252, 244, 244);
  font-size: 1.3em;
  display: flex;
  align-items: center;
  padding-left: 20px;
}
main {
  height: 85%;
}
</style>
