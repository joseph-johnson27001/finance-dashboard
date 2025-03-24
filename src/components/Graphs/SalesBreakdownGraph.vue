<template>
  <div class="chart-container">
    <div class="header">
      <h4>Sales Breakdown</h4>
    </div>
    <apexchart
      ref="chart"
      type="pie"
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
      chartOptions: {
        chart: {
          id: "sales-breakdown-pie-chart",
          toolbar: { show: false },
          fontFamily: "Inter, sans-serif",
        },
        labels: ["Product A", "Product B", "Product C", "Product D"],
        colors: ["#2980B9", "#FF5722", "#4CAF50", "#FFC107"],
        responsive: [
          {
            options: {
              chart: {
                width: "100%",
              },
              legend: {
                position: "bottom",
              },
            },
          },
        ],
        legend: {
          show: false,
        },
        dataLabels: {
          enabled: true,
          formatter: function (val, opts) {
            return `${opts.w.config.labels[opts.seriesIndex]}: ${val.toFixed(
              1
            )}%`;
          },
          style: {
            fontSize: "14px",
            fontWeight: "500",
            colors: ["#fff"],
          },
        },
      },
      series: [55, 25, 15, 5],
    };
  },
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
