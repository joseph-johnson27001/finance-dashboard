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
      <div class="charts-container">
        <!-- REVENUE GRAPH INSIDE CARD -->
        <CardContainer>
          <RevenueExpensesGraph />
        </CardContainer>
        <CardContainer>
          <SalesBreakdownGraph />
        </CardContainer>
      </div>
    </div>
  </div>
</template>

<script>
import SideBar from "./components/Navigation/SideBar.vue";
import CardContainer from "./components/UI/CardContainer.vue";
import RevenueExpensesGraph from "./components/Graphs/RevenueExpensesGraph.vue";
import SalesBreakdownGraph from "./components/Graphs/SalesBreakdownGraph.vue";

export default {
  name: "App",
  components: {
    SideBar,
    CardContainer,
    RevenueExpensesGraph,
    SalesBreakdownGraph,
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

h4 {
  color: #274472;
  padding: 2px;
  margin: 2px;
  font-weight: 500;
}

.kpis-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
  margin-bottom: 10px;
}

.charts-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
  margin-bottom: 10px;
}
</style>
