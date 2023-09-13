<script setup lang="ts">
import { ref } from "vue";
import { Title } from "../atoms";

const chartOptions = ref({
  chart: {
    height: 350,
    type: "radialBar",
    toolbar: {
      show: false,
    },
  },
  plotOptions: {
    radialBar: {
      startAngle: -135,
      endAngle: 225,
      hollow: {
        margin: 0,
        size: "70%",
        background: "#fff",
        image: undefined,
        imageOffsetX: 0,
        imageOffsetY: 0,
        position: "front",
        dropShadow: {
          enabled: true,
          top: 3,
          left: 0,
          blur: 4,
          opacity: 0.24,
        },
      },
      track: {
        background: "#fff",
        strokeWidth: "85%",
        margin: 0,
        dropShadow: {
          enabled: true,
          top: -3,
          left: 0,
          blur: 4,
          opacity: 0.35,
        },
      },

      dataLabels: {
        show: true,
        name: {
          offsetY: -10,
          show: false,
          color: "#888",
          fontSize: "0",
        },
        value: {
          formatter: function (val: number) {
            return `${val[0]},${val[1]}/10`;
          },
          color: "#F3705A",
          fontSize: "48px",
          fontWeight: "bold",
          show: true,
        },
      },
    },
  },
  fill: {
    type: "gradient",
    gradient: {
      shade: "dark",
      type: "horizontal",
      shadeIntensity: 0.5,
      gradientToColors: ["#F3705A"],
      inverseColors: true,
      opacityFrom: 1,
      opacityTo: 1,
      stops: [0, 50, 100],
    },
  },
  stroke: {
    lineCap: "round",
  },
});

const series = ref(["75"]);
</script>

<template>
  <main class="main-container">
    <Title>Comércio varejista de artigos do vestuário e acessórios</Title>
    <div id="card">
      <div id="chart">
        <apexchart
          type="radialBar"
          height="350"
          :options="chartOptions"
          :series="series"
        ></apexchart>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
.main-container {
  padding-top: 40px;
}
</style>
