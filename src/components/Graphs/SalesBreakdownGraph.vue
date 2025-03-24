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
          position: "right",
          offsetY: 0,
          labels: {
            colors: "rgba(47, 43, 61, 0.9)",
            formatter: function (val, opts) {
              const percentage = opts.w.globals.series[opts.seriesIndex];
              const total = opts.w.globals.seriesTotals[opts.seriesIndex];
              const value = ((percentage / total) * 100).toFixed(1);
              return `${val}: ${value}%`;
            },
          },
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
  methods: {
    triggerResize() {
      this.$nextTick(() => {
        if (this.$refs.chart) {
          this.$refs.chart.chart.resize();
        }
      });
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

h4 {
  color: #274472;
  padding: 2px;
  margin: 2px;
  font-weight: 500;
}
</style>
