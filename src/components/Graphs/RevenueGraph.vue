<template>
  <div>
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

        title: {
          text: "Monthly Revenue",
          align: "left",
        },
        colors: ["#3b82f6"],
        grid: {
          borderColor: "#e0e0e0",
          strokeDashArray: 5,
        },
      },
      series: [
        {
          name: "Revenue",
          data: [
            10000, 12000, 15000, 14000, 18000, 20000, 22000, 21000, 23000,
            25000, 27000, 30000,
          ],
        },
      ],
    };
  },
};
</script>
