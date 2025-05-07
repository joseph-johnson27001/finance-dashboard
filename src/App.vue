<template>
  <div id="app">
    <SideBar />
    <div class="main">
      <TopCard />
      <div class="kpis-container">
        <KPIContainer
          v-for="(kpi, index) in kpis"
          :key="index"
          :iconClass="kpi.iconClass"
          :kpiName="kpi.name"
          :value="kpi.value"
        />
      </div>
      <div class="charts-container">
        <CardContainer v-for="(chart, index) in charts" :key="index">
          <component :is="chart.component" />
        </CardContainer>
      </div>
    </div>
    <DashboardButton />
  </div>
</template>

<script>
import SideBar from "./components/Navigation/SideBar.vue";
import TopCard from "./components/UI/TopCard.vue";
import KPIContainer from "./components/UI/KPIContainer.vue";
import CardContainer from "./components/UI/CardContainer.vue";
import RevenueExpensesGraph from "./components/Graphs/RevenueExpensesGraph.vue";
import SalesBreakdownGraph from "./components/Graphs/SalesBreakdownGraph.vue";
import OperatingExpensesGraph from "./components/Graphs/OperatingExpensesGraph.vue";
import ProfitMarginGraph from "./components/Graphs/ProfitMarginGraph.vue";
import DashboardButton from "./components/UI/DashboardButton.vue";

export default {
  name: "App",
  components: {
    SideBar,
    CardContainer,
    RevenueExpensesGraph,
    SalesBreakdownGraph,
    KPIContainer,
    TopCard,
    OperatingExpensesGraph,
    ProfitMarginGraph,
    DashboardButton,
  },
  data() {
    return {
      kpis: [
        {
          iconClass: "fas fa-dollar-sign",
          name: "Total Revenue",
          value: "$1,234,567",
        },
        {
          iconClass: "fas fa-credit-card",
          name: "Net Profit",
          value: "$456,789",
        },
        {
          iconClass: "fas fa-chart-line",
          name: "Gross Margin",
          value: "25%",
        },
        {
          iconClass: "fas fa-building",
          name: "Operating Expenses",
          value: "$123,456",
        },
        {
          iconClass: "fas fa-money-bill-wave",
          name: "Cash Flow",
          value: "$89,000",
        },
        {
          iconClass: "fas fa-calendar-check",
          name: "Accounts Receivable",
          value: "$150,000",
        },
        {
          iconClass: "fas fa-calendar-times",
          name: "Accounts Payable",
          value: "$78,000",
        },
        {
          iconClass: "fas fa-balance-scale",
          name: "Current Ratio",
          value: "1.5",
        },
        {
          iconClass: "fas fa-cogs",
          name: "EBITDA",
          value: "$345,678",
        },
        {
          iconClass: "fas fa-hand-holding-usd",
          name: "Debt to Equity Ratio",
          value: "1.2",
        },
      ],
      charts: [
        {
          component: RevenueExpensesGraph,
        },
        {
          component: OperatingExpensesGraph,
        },
        {
          component: ProfitMarginGraph,
        },
        {
          component: SalesBreakdownGraph,
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
  padding: 20px;
  height: 100%;
  width: 100%;
  overflow-y: scroll;
}

h4 {
  color: #274472;
  padding: 2px;
  margin: 2px;
  font-weight: 400;
}

.kpis-container {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 10px;
  margin-bottom: 20px;
  margin-top: 20px;
}

.charts-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
  margin-bottom: 30px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: -10px;
}

select {
  font-family: "Assistant";
  outline: none;
  padding: 10px 5px;
  font-size: 14px;
  border-radius: 5px;
  border: 1px solid #ddd;
}

@media (max-width: 1000px) {
  .kpis-container {
    grid-template-columns: repeat(2, 1fr);
  }
  .charts-container {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 500px) {
  .kpis-container {
    grid-template-columns: 1fr;
  }
}
</style>
