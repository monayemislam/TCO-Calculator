<!-- <template>
  <canvas ref="chartCanvas"></canvas>
</template>
    
  <script>
import { defineComponent } from "vue";
import {
  Chart,
  BarController,
  CategoryScale,
  LinearScale,
  BarElement,
  Tooltip,
} from "chart.js";

export default defineComponent({
  props: {
    chartData: {
      type: Object,
      required: true,
    },
  },
  mounted() {
    this.renderChart();
  },
  methods: {
    renderChart() {
      Chart.register(
        BarController,
        CategoryScale,
        LinearScale,
        BarElement,
        Tooltip
      );

      new Chart(this.$refs.chartCanvas, {
        type: "bar",
        data: {
          labels: this.chartData.labels,
          datasets: [
            {
              label: "Tco Comparison",
              data: this.chartData.values,
              backgroundColor: [
                "rgba(255, 99, 132, 0.6)", // Red
                "rgba(54, 162, 235, 0.6)", // Blue
                "rgba(255, 206, 86, 0.6)", // Yellow
              ],
              borderColor: [
                "rgba(255, 99, 132, 1)", // Red
                "rgba(54, 162, 235, 1)", // Blue
                "rgba(255, 206, 86, 1)", // Yellow
              ],
              borderWidth: 1,
              barThickness: "flex",
              categoryPercentage: 1,
            },
          ],
        },
        options: {
          responsive: true,
          plugins: {
            tooltip: {
              enabled: true,
            },
          },
          scales: {
            x: {
              display: true,
              grid: {
                display: false,
              },
            },
            y: {
              display: true,
              grid: {
                display: true,
              },
            },
          },
        },
      });
    },
  },
});
</script>
   -->




   <template>
  <canvas ref="chartCanvas"></canvas>
</template>
  
  <script>
import { defineComponent } from "vue";
import {
  Chart,
  BarController,
  CategoryScale,
  LinearScale,
  BarElement,
  Tooltip,
} from "chart.js";

export default defineComponent({
  props: {
    chartData: {
      type: Object,
      required: true,
    },
  },
  mounted() {
    this.renderChart();
  },
  watch: {
    chartData: {
      deep: true,
      handler(newChartData) {
        this.updateChart(newChartData);
      },
    },
  },
  methods: {
    renderChart() {
      Chart.register(
        BarController,
        CategoryScale,
        LinearScale,
        BarElement,
        Tooltip
      );

      this.chartInstance = new Chart(this.$refs.chartCanvas, {
        type: "bar",
        data: {
          labels: this.chartData.labels,
          datasets: [
            {
              // label: "Tco Comparison",
              data: this.chartData.values,
              backgroundColor: [
                "rgba(255, 99, 132, 0.6)", // Red
                "rgba(54, 162, 235, 0.6)", // Blue
                "rgba(255, 206, 86, 0.6)", // Yellow
              ],
              borderColor: [
                "rgba(255, 99, 132, 1)", // Red
                "rgba(54, 162, 235, 1)", // Blue
                "rgba(255, 206, 86, 1)", // Yellow
              ],
              borderWidth: 1,
              barThickness: "flex",
              categoryPercentage: 1,
            },
          ],
        },
        options: {
          responsive: true,
          plugins: {
            tooltip: {
              enabled: true,
            },
          },
          scales: {
            x: {
              display: true,
              grid: {
                display: false,
              },
            },
            y: {
              display: true,
              grid: {
                display: true,
              },
            },
          },
        },
      });
    },
    updateChart(newChartData) {
      if (this.chartInstance) {
        this.chartInstance.data.labels = newChartData.labels;
        this.chartInstance.data.datasets[0].data = newChartData.values;
        this.chartInstance.update();
      }
    },
  },
});
</script>
  