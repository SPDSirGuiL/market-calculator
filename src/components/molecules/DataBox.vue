<script setup lang="ts">
interface DataBoxProps {
  text: string;
  percent: number;
}

const props = defineProps<DataBoxProps>();

const formatNumber = (percent: number) => {
  if (percent > 0) {
    return `+ ${percent}%`;
  }

  const percentString = String(percent);
  return `- ${percentString.replace("-", "")}%`;
};
</script>

<template>
  <div class="box">
    <span class="title">{{ props.text }}</span>

    <div class="percent-container">
      <span :class="`percent ${percent > 0 ? 'positive' : 'negative'}`">
        {{ formatNumber(props.percent) }}
      </span>
      <q-icon
        :name="percent > 0 ? 'img:/up.svg' : 'img:/down.svg'"
        size="2rem"
      />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.box {
  border-radius: 16px;
  box-shadow: 0px 0px 4px 0px rgba(0, 0, 0, 0.25);

  padding: 10px;

  .title {
    overflow: hidden;
    color: #5f6a6c;
    text-overflow: ellipsis;
    font-family: "Roboto";
    font-size: 1.25rem;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
  }

  .percent-container {
    display: flex;
    align-items: center;

    margin-top: 14px;

    .percent {
      font-family: "Roboto";
      font-size: 2rem;
      font-style: normal;
      font-weight: 700;
      line-height: 2rem;

      margin-right: 10px;

      &.positive {
        color: #99ca3c;
      }

      &.negative {
        color: #f3705a;
      }
    }
  }
}
</style>
