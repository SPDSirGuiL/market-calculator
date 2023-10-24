<script setup lang="ts"></script>

<template>
  <footer>
    <div class="tab">
      <q-icon />
      <span>Aquecimento</span>
    </div>

    <div class="tab">
      <q-icon />
      <span>Gráficos</span>
    </div>

    <div class="tab">
      <q-icon />
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

    span {
      color: #f3705a;
      font-family: "Roboto";
      font-size: 0.75rem;
      font-style: normal;
      font-weight: 400;
      line-height: 0.875rem;
    }
  }
}
</style>
