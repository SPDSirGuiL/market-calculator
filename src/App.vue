<script setup lang="ts">
import { ref } from "vue";
import { FilterMenu } from "./components/molecules";
import { Header, Main, Drawer } from "./components/organisms";

const enableFilterMenu = ref(false);

const drawer = ref(true);

const menuList = [
  {
    icon: "inbox",
    label: "Inbox",
    separator: true,
  },
  {
    icon: "send",
    label: "Outbox",
    separator: false,
  },
  {
    icon: "delete",
    label: "Trash",
    separator: false,
  },
  {
    icon: "error",
    label: "Spam",
    separator: true,
  },
  {
    icon: "settings",
    label: "Settings",
    separator: false,
  },
  {
    icon: "feedback",
    label: "Send Feedback",
    separator: false,
  },
  {
    icon: "help",
    iconColor: "primary",
    label: "Help",
    separator: false,
  },
];

const openMenu = () => {
  enableFilterMenu.value = true;
};

const closeMenu = () => {
  enableFilterMenu.value = false;
};
</script>

<template>
  <q-layout container class="main-container">
    <Drawer :open="drawer" />

    <Header @openMenu="openMenu" />
    <Main :drawerOpened="drawer" />
  </q-layout>
</template>

<style lang="scss" scoped>
.main-container {
  height: 100vh;

  .main-drawer {
    width: 100vw;
  }
}
</style>
