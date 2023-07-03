<template>
  <div class="chart-container">
    <Bar id="my-chart-id" :options="chartOptions" :data="chartData" />
  </div>
</template>
  
  <script>
import { Bar } from "vue-chartjs";
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from "chart.js";

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
);

export default {
  name: "BarChart",
  components: { Bar },
  data() {
    return {
      chartData: {
        labels: ["January", "February", "March", "April", "May"],
        datasets: [
          {
            label: "Data One",
            backgroundColor: "#02A88F",
            data: [12000, 20, 4012, -23],
          },
          {
            label: "Data Two",
            backgroundColor: "#0387AD",
            data: [4000, 6030, -7332, -23],
          },
          {
            label: "Data Three",
            backgroundColor: "#005FAA",
            data: [2000, 20, 602, -23],
          },
          {
            backgroundColor: "#005FAA",
            data: [900, 20, 5602, -93],
          },
        ],
      },
      chartOptions: {
        plugins: {
          title: {
            display: true,
            text: "Chart.js Bar Chart - Stacked",
          },
        },
        responsive: true,
        height: 550,
        width: 450,
        scales: {
          x: {
            stacked: true,
          },
          y: {
            stacked: true,
          },
        },
      },
    };
  },
};
</script>

<style scoped>
.chart-container {
  margin: 0 auto;
}
</style>