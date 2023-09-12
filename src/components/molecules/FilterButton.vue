<script setup lang="ts"></script>

<template>
  <q-btn flat no-caps rounded class="filter-btn" :ripple="false">
    <q-icon name="o_tune" size="2rem" />
    <span> Filtros </span>
  </q-btn>
</template>

<style lang="scss" scoped>
.filter-btn {
  color: #5f6a6c;
  font-family: "Roboto";

  span {
    font-size: 1.15rem;
    margin-left: 10px;
  }
}
</style>
