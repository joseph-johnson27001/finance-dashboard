<template>
  <div class="chart-container">
    <h4>Revenue</h4>
    <apexchart
      type="line"
      height="350"
      :options="chartOptions"
      :series="series"
    >
    </apexchart>
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
      chartOptions: {
        chart: {
          id: "revenue-line-chart",
          toolbar: { show: false },
          fontFamily: "Inter, sans-serif",
        },
        xaxis: {
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
        },
        colors: ["#ffad5f"],
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
      ],
    };
  },
  mounted() {
    setTimeout(() => {
      this.series = [
        {
          name: "Revenue",
          data: [
            10000, 12000, 15000, 14000, 18000, 20000, 22000, 21000, 23000,
            25000, 27000, 30000,
          ],
        },
      ];
    }, 100);
  },
};
</script>

<style scoped></style>
