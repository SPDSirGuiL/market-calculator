<script setup lang="ts">
import { ref } from "vue";
import { FilterMenu } from "./components/molecules";
import { Header, Main, Drawer, Footer } from "./components/organisms";
import { selectedTabType } from "./@types/tabsTypes";

const drawer = ref(false);

const selectedTab = ref<selectedTabType>("heating");

const openMenu = () => {
  drawer.value = true;
};

const closeDrawer = () => {
  drawer.value = false;
};

const updateTab = (tab: selectedTabType) => {
  selectedTab.value = tab;
};
</script>

<template>
  <q-layout container class="main-container">
    <Header @openMenu="openMenu" />
    <Main :drawerOpened="drawer" />
  </q-layout>

  <Drawer :open="drawer" @closeDrawer="closeDrawer" />

  <Footer :selectedTab="selectedTab" @updateTab="updateTab" />
</template>

<style lang="scss" scoped>
.main-container {
  height: calc(100vh - 94px);

  .main-drawer {
    width: 100vw;
  }
}
</style>
