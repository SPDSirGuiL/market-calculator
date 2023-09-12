<script setup lang="ts">
import { ref } from "vue";
import { FilterMenu } from "./components/molecules";
import { Header, Main } from "./components/organisms";

const enableFilterMenu = ref(false);

const openMenu = () => {
  enableFilterMenu.value = true;
};

const closeMenu = () => {
  enableFilterMenu.value = false;
};
</script>

<template>
  <FilterMenu :able="enableFilterMenu" @closeMenu="closeMenu" />
  <Header @openMenu="openMenu" />
  <Main />
</template>

<style scoped></style>
