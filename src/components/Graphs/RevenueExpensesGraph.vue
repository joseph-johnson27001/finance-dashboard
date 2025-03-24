<template>
  <div class="chart-container">
    <div class="header">
      <h4>Revenue / Expenses</h4>
      <!-- Dropdown for selecting time range -->
      <select v-model="selectedRange" @change="updateChartData">
        <option value="7d">Last 7 Days</option>
        <option value="12m">Last 12 Months</option>
        <option value="5y">Last 5 Years</option>
      </select>
    </div>
    <apexchart
      type="line"
      height="350"
      :options="chartOptions"
      :series="series"
    ></apexchart>
  </div>
</template>

<script>
import VueApexCharts from "vue3-apexcharts";

export default {
  components: {
    apexchart: VueApexCharts,
  },
  data() {
    return {
      selectedRange: "12m",
      chartOptions: {
        chart: {
          id: "revenue-expenses-line-chart",
          toolbar: { show: false },
          fontFamily: "Inter, sans-serif",
        },
        xaxis: {
          categories: [],
          labels: {
            style: {
              colors: "rgba(47, 43, 61, 0.9)",
            },
          },
        },
        yaxis: {
          labels: {
            style: {
              colors: "rgba(47, 43, 61, 0.9)",
            },
          },
        },
        colors: ["#2980B9", "#FF5722"],
        grid: {
          borderColor: "#e0e0e0",
          strokeDashArray: 0,
          xaxis: {
            lines: { show: true },
          },
          yaxis: {
            lines: { show: true },
          },
        },
      },
      series: [
        {
          name: "Revenue",
          data: [],
        },
        {
          name: "Expenses",
          data: [],
        },
      ],
      dataSets: {
        "7d": {
          categories: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
          revenueData: [5100, 6200, 5500, 7400, 7200, 6700, 7550],
          expensesData: [3200, 3600, 3400, 4200, 4300, 4000, 4200],
        },
        "12m": {
          categories: [
            "Jan",
            "Feb",
            "Mar",
            "Apr",
            "May",
            "Jun",
            "Jul",
            "Aug",
            "Sep",
            "Oct",
            "Nov",
            "Dec",
          ],
          revenueData: [
            10000, 12500, 14500, 13500, 18500, 19800, 22500, 21500, 24000,
            26500, 27500, 31000,
          ],
          expensesData: [
            8100, 8800, 9200, 9600, 10100, 11300, 12200, 11800, 13000, 13500,
            14500, 15500,
          ],
        },
        "5y": {
          categories: ["2019", "2020", "2021", "2022", "2023"],
          revenueData: [48500, 59000, 72500, 82500, 95000],
          expensesData: [36000, 40500, 46000, 53000, 58500],
        },
      },
    };
  },
  mounted() {
    this.updateChartData();
  },
  methods: {
    updateChartData() {
      const selectedData = this.dataSets[this.selectedRange];
      this.series = [
        {
          name: "Revenue",
          data: selectedData.revenueData,
        },
        {
          name: "Expenses",
          data: selectedData.expensesData,
        },
      ];
      this.chartOptions.xaxis.categories = selectedData.categories;
    },
  },
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

select {
  font-family: "Inter" sans-serif;
  outline: none;
  padding: 10px 5px;
  font-size: 14px;
  border-radius: 5px;
  border: 1px solid #ddd;
}
</style>
