<script setup lang="ts">
import { ref } from "vue";
import { FilterMenu } from "./components/molecules";
import { Header, Main, Drawer, Footer } from "./components/organisms";
import { selectedTabType } from "./@types/tabsTypes";

const drawer = ref(false);
const drawerVisible = ref(false);

const selectedTab = ref<selectedTabType>("heating");

const openMenu = () => {
  drawerVisible.value = true;
  setTimeout(() => {
    drawer.value = true;
  }, 100);
};

const closeDrawer = () => {
  drawer.value = false;

  setTimeout(() => {
    drawerVisible.value = false;
  }, 500);
};

const updateTab = (tab: selectedTabType) => {
  selectedTab.value = tab;
};
</script>

<template>
  <q-layout container class="main-container">
    <Header @openMenu="openMenu" />
    <Main />
  </q-layout>

  <Drawer v-if="drawerVisible" :open="drawer" @closeDrawer="closeDrawer" />

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
