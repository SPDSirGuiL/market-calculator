<script setup lang="ts"></script>

<template>
  <div class="box">
    <span class="title">Crescimento de receita</span>

    <div class="percent-container">
      <span class="percent">+ 12%</span>
      <q-icon name="img:/up.svg" size="2rem" />
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
      color: #99ca3c;
      font-family: "Roboto";
      font-size: 2rem;
      font-style: normal;
      font-weight: 700;
      line-height: 2rem;
    }
  }
}
</style>
