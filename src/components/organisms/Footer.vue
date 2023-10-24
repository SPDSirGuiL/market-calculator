<script setup lang="ts">
import { selectedTabType } from "../../@types/tabsTypes";

interface FooterProps {
  selectedTab: selectedTabType;
}

const props = defineProps<FooterProps>();

const emit = defineEmits(["updateTab"]);

const updateTab = (tab: selectedTabType) => {
  emit("updateTab", tab);
};
</script>

<template>
  <footer>
    <div
      @click="updateTab('heating')"
      :class="`tab ${props.selectedTab == 'heating' && 'heat'}`"
    >
      <q-icon
        :name="
          props.selectedTab == 'heating'
            ? 'img:/heat.svg'
            : 'img:/unselected-heat.svg'
        "
        size="2.5rem"
      />
      <span>Aquecimento</span>
    </div>

    <div
      @click="updateTab('charts')"
      :class="`tab ${props.selectedTab == 'charts' && 'charts'}`"
    >
      <q-icon
        :name="
          props.selectedTab == 'charts'
            ? 'img:/chart.svg'
            : 'img:/unselected-chart.svg'
        "
        size="2.5rem"
      />
      <span>Gráficos</span>
    </div>

    <div
      @click="updateTab('ranking')"
      :class="`tab ${props.selectedTab == 'ranking' && 'ranking'}`"
    >
      <q-icon
        :name="
          props.selectedTab == 'ranking'
            ? 'img:/medal.svg'
            : 'img:/unselected-medal.svg'
        "
        size="2.5rem"
      />
      <span>Ranking</span>
    </div>
  </footer>
</template>

<style lang="scss" scoped>
footer {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  height: 94px;
  width: 100%;
  border-top: 1px solid #eee;

  .tab {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    cursor: pointer;

    color: #95a5a6;

    &.heat {
      color: #f3705a;
    }

    &.charts {
      color: #99ca3c;
    }

    &.ranking {
      color: #ffbf1e;
    }

    span {
      font-family: "Roboto";
      font-size: 0.75rem;
      font-style: normal;
      font-weight: 400;
      line-height: 0.875rem;
    }
  }
}
</style>
