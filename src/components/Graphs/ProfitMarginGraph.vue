<template>
  <div class="chart-container">
    <div class="header">
      <h4>Profit Margin</h4>
      <select v-model="selectedRange">
        <option value="7d">7 Days</option>
        <option value="12m">12 Months</option>
        <option value="5y">5 Years</option>
      </select>
    </div>
    <apexchart
      type="line"
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
      selectedRange: "12m",
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
          categories: ["2021", "2022", "2023", "2024", "2025"],
          revenueData: [48500, 59000, 72500, 82500, 95000],
          expensesData: [36000, 40500, 46000, 53000, 58500],
        },
      },
    };
  },
  computed: {
    chartOptions() {
      return {
        chart: {
          id: "profit-margin-line-chart",
          toolbar: { show: false },
          fontFamily: "Inter, sans-serif",
          zoom: {
            enabled: false,
          },
          animations: {
            enabled: true,
            easing: "easeinout",
            speed: 400,
          },
        },
        xaxis: {
          categories: this.dataSets[this.selectedRange].categories,
        },
        yaxis: {
          labels: {
            formatter: (value) => `${(value * 100).toFixed(2)}%`,
          },
        },

        colors: ["#2980B9"],
        grid: {
          borderColor: "#e0e0e0",
          strokeDashArray: 0,
        },
      };
    },
    series() {
      const selectedData = this.dataSets[this.selectedRange];
      const profitMarginData = selectedData.revenueData.map(
        (revenue, index) =>
          (revenue - selectedData.expensesData[index]) / revenue
      );
      return [
        {
          name: "Profit Margin",
          data: profitMarginData,
        },
      ];
    },
  },
};
</script>
