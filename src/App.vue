<template>
  <div id="app">
    <SideBar />
    <div class="main">
      <div>hello</div>
    </div>
  </div>
</template>

<script>
import SideBar from "./components/Navigation/SideBar.vue";

export default {
  name: "App",
  components: {
    SideBar,
  },
};
</script>

<style>
body {
  margin: 0px !important;
  scrollbar-width: none;
  font-family: "Inter", sans-serif;
  overflow-y: hidden;
}

::-webkit-scrollbar {
  display: none;
}
</style>

<style scoped>
body {
  padding: 0;
  margin: 0;
}

#app {
  display: flex;
  flex-direction: row;
  font-family: "Inter", sans-serif;
  height: 100dvh;
  width: 100%;
}

.main {
  flex-grow: 1;
  background-color: #f8f7fa;
  padding: 10px;
  height: 100%;
  width: 100%;
}
</style>
