<template>
  <div class="chart-container">
    <div class="header">
      <h4>Operating Expenses by Month</h4>
      <select v-model="selectedRange">
        <option value="7d">Last 7 Days</option>
        <option value="12m">Last 12 Months</option>
        <option value="5y">Last 5 Years</option>
      </select>
    </div>
    <apexchart
      type="bar"
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
      dataSets: {
        "7d": {
          categories: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
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
          expensesData: [
            8100, 8800, 9200, 9600, 10100, 11300, 12200, 11800, 13000, 13500,
            14500, 15500,
          ],
        },
        "5y": {
          categories: ["2021", "2022", "2023", "2024", "2025"],
          expensesData: [36000, 40500, 46000, 53000, 58500],
        },
      },
    };
  },
  computed: {
    chartOptions() {
      return {
        chart: {
          id: "operating-expenses-bar-chart",
          toolbar: { show: false },
          fontFamily: "Inter, sans-serif",
        },
        xaxis: {
          categories: this.dataSets[this.selectedRange].categories,
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
        colors: ["#FF5722"],
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
      };
    },
    series() {
      const selectedData = this.dataSets[this.selectedRange];
      return [
        {
          name: "Operating Expenses",
          data: selectedData.expensesData,
        },
      ];
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
