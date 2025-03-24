<template>
  <div id="app">
    <SideBar />
    <div class="main">
      <div class="kpis-container">
        <!-- KPIs will go here -->
        <CardContainer> </CardContainer>
        <CardContainer> </CardContainer>
        <CardContainer> </CardContainer>
        <CardContainer> </CardContainer>
        <CardContainer> </CardContainer>
        <CardContainer> </CardContainer>
        <CardContainer> </CardContainer>
        <CardContainer> </CardContainer>
      </div>
      <div class="revenue-graph-container">
        <!-- REVENUE GRAPH INSIDE CARD -->
        <CardContainer>
          <RevenueGraph />
        </CardContainer>
      </div>
    </div>
  </div>
</template>

<script>
import SideBar from "./components/Navigation/SideBar.vue";
import CardContainer from "./components/UI/CardContainer.vue";
import RevenueGraph from "./components/Graphs/RevenueGraph.vue";

export default {
  name: "App",
  components: {
    SideBar,
    CardContainer,
    RevenueGraph,
  },
};
</script>

<style>
body {
  margin: 0px !important;
  scrollbar-width: none;
  font-family: "Inter", sans-serif;
  overflow-y: hidden;
  color: #333;
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

.kpis-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
  margin-bottom: 10px;
}
</style>
