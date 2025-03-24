<template>
  <div id="app">
    <SideBar />
    <div class="main">
      <TopCard />
      <div class="kpis-container">
        <!-- Loop through KPIs -->
        <KPIContainer
          v-for="(kpi, index) in kpis"
          :key="index"
          :iconClass="kpi.iconClass"
          :kpiName="kpi.name"
          :value="kpi.value"
        />
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
import TopCard from "./components/UI/TopCard.vue";
import KPIContainer from "./components/UI/KPIContainer.vue";
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
    KPIContainer,
    TopCard,
  },
  data() {
    return {
      kpis: [
        {
          iconClass: "fas fa-dollar-sign", // Icon for total revenue
          name: "Total Revenue",
          value: "$1,234,567",
        },
        {
          iconClass: "fas fa-credit-card", // Icon for net profit
          name: "Net Profit",
          value: "$456,789",
        },
        {
          iconClass: "fas fa-chart-line", // Icon for gross margin
          name: "Gross Margin",
          value: "25%",
        },
        {
          iconClass: "fas fa-building", // Icon for operating expenses
          name: "Operating Expenses",
          value: "$123,456",
        },
        {
          iconClass: "fas fa-money-bill-wave", // Icon for cash flow
          name: "Cash Flow",
          value: "$89,000",
        },
        {
          iconClass: "fas fa-calendar-check", // Icon for accounts receivable
          name: "Accounts Receivable",
          value: "$150,000",
        },
        {
          iconClass: "fas fa-calendar-times", // Icon for accounts payable
          name: "Accounts Payable",
          value: "$78,000",
        },
        {
          iconClass: "fas fa-balance-scale", // Icon for current ratio
          name: "Current Ratio",
          value: "1.5",
        },
        {
          iconClass: "fas fa-cogs", // Icon for EBITDA
          name: "EBITDA",
          value: "$345,678",
        },
        {
          iconClass: "fas fa-hand-holding-usd", // Icon for debt to equity ratio
          name: "Debt to Equity Ratio",
          value: "1.2",
        },
      ],
    };
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

.kpis-container {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
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
