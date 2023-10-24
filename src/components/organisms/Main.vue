<script setup lang="ts">
import { ref } from "vue";
import { Title } from "../atoms";
import { DataBox } from "../molecules";

interface MainProps {
  drawerOpened: boolean;
}

const props = defineProps<MainProps>();

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
        strokeWidth: "50%",
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
  <main :class="`main-container ${props.drawerOpened && 'no-scroll'}`">
    <Title>Comércio varejista de artigos do vestuário e acessórios</Title>
    <div id="card">
      <div id="chart">
        <apexchart
          type="radialBar"
          height="350"
          :options="chartOptions"
          :series="series"
        ></apexchart>

        <div class="data-container">
          <span class="title">Aquecimento de mercado</span>

          <div class="container">
            <DataBox text="Crescimento de receita" :percent="12" />
            <DataBox text="Empresas abertas x fechadas" :percent="-5" />
            <DataBox text="Crescimento de lucro" :percent="35" />
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
.main-container {
  padding: 40px 20px 0 20px;

  .data-container {
    display: flex;
    flex-direction: column;
    justify-content: center;

    border-radius: 16px;
    box-shadow: 0px 0px 4px 0px rgba(0, 0, 0, 0.25);

    padding: 10px;

    margin-top: -140px;

    .title {
      color: #5f6a6c;
      text-align: center;
      font-family: "Roboto";
      font-size: 1.25rem;
      font-style: normal;
      font-weight: 400;
      line-height: normal;

      margin-top: 115px;
    }

    .container {
      display: flex;
      flex-direction: column;

      margin: 70px 0 20px 0;
      gap: 28px;
    }
  }
}

.no-scroll {
  max-height: calc(100vh - 36px);
  max-width: 100vw;

  overflow: hidden;
}
</style>
