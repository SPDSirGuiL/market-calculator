<script setup lang="ts"></script>

<template>
  <q-btn flat no-caps rounded class="filter-btn" :ripple="false">
    <span> Filtros </span>
    <q-icon name="o_filter_list" size="2.5rem" />
  </q-btn>
</template>

<style lang="scss" scoped>
.filter-btn {
  color: #5f6a6c;
  font-family: "Roboto";

  span {
    margin-right: 10px;

    font-size: 1.5rem;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
  }
}
</style>
