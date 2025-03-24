<template>
  <div class="chart-container">
    <div class="header">
      <h4>Sales by Product</h4>
      <select v-model="selectedTimePeriod">
        <option value="7d">Last 7 Days</option>
        <option value="12m">Last 12 Months</option>
        <option value="5y">Last 5 Years</option>
      </select>
    </div>
    <apexchart
      type="bar"
      height="300"
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
      selectedTimePeriod: "12m",
      dataSets: {
        "7d": {
          categories: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
          series: [
            {
              name: "Product A",
              data: [1000, 1200, 1500, 1800, 2000, 2200, 2500],
            },
            { name: "Product B", data: [500, 600, 700, 800, 1000, 1200, 1500] },
            { name: "Product C", data: [400, 450, 600, 750, 900, 1050, 1200] },
            { name: "Product D", data: [300, 350, 400, 450, 500, 600, 700] },
          ],
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
          series: [
            {
              name: "Product A",
              data: [
                8100, 8800, 9200, 9600, 10100, 11300, 12200, 11800, 13000,
                13500, 14500, 15500,
              ],
            },
            {
              name: "Product B",
              data: [
                4000, 4500, 5000, 5500, 6000, 6200, 7000, 7400, 7800, 8100,
                8500, 8900,
              ],
            },
            {
              name: "Product C",
              data: [
                3000, 3100, 3300, 3500, 3700, 3900, 4200, 4400, 4700, 5000,
                5300, 5600,
              ],
            },
            {
              name: "Product D",
              data: [
                2000, 2300, 2500, 2700, 2900, 3100, 3300, 3500, 3700, 3900,
                4200, 4500,
              ],
            },
          ],
        },
        "5y": {
          categories: ["2021", "2022", "2023", "2024", "2025"],
          series: [
            { name: "Product A", data: [36000, 40500, 46000, 53000, 58500] },
            { name: "Product B", data: [22000, 25000, 28000, 32000, 36000] },
            { name: "Product C", data: [14000, 16000, 18000, 20000, 22000] },
            { name: "Product D", data: [9000, 10000, 11000, 12000, 14000] },
          ],
        },
      },
    };
  },
  computed: {
    chartOptions() {
      return {
        chart: {
          id: "sales-bar-chart",
          toolbar: { show: false },
          fontFamily: "Inter, sans-serif",
        },
        xaxis: {
          categories: this.dataSets[this.selectedTimePeriod].categories,
          labels: { style: { colors: "rgba(47, 43, 61, 0.9)" } },
        },
        yaxis: {
          labels: { style: { colors: "rgba(47, 43, 61, 0.9)" } },
        },
        colors: ["#FF5722", "#03A9F4", "#4CAF50", "#FFC107"],
        grid: {
          borderColor: "#e0e0e0",
          strokeDashArray: 0,
          xaxis: { lines: { show: true } },
          yaxis: { lines: { show: true } },
        },
        legend: { show: true },
        dataLabels: { enabled: false },
        tooltip: {
          y: {
            formatter: (val) => `$${val.toFixed(2)}`,
          },
        },
      };
    },
    series() {
      return this.dataSets[this.selectedTimePeriod].series;
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
  font-family: "Inter", sans-serif;
  outline: none;
  padding: 10px 5px;
  font-size: 14px;
  border-radius: 5px;
  border: 1px solid #ddd;
}
</style>
