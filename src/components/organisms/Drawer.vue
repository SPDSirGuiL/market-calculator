<script setup lang="ts">
import { ref } from "vue";
import { DrawerHeader, DrawerBody, Notification } from "../molecules";

interface DrawerProps {
  open: boolean;
}

const props = defineProps<DrawerProps>();

const notification = ref(false);

const openNotification = () => {
  notification.value = true;
};
</script>

<template>
  <div :class="`drawer-container ${open ? 'opened' : 'closed'}`">
    <DrawerHeader />

    <DrawerBody @openNotification="openNotification" />
  </div>

  <q-dialog v-model="notification">
    <Notification>
      Deseja importar sua localização? Ao importar sua localização, economizamos
      seu tempo para fazer a busca
    </Notification>
  </q-dialog>
</template>

<style lang="scss" scoped>
.drawer-container {
  width: 100vw;
  height: 100vh;

  position: absolute;
  top: 0;

  z-index: 999;

  background: #fff;

  transition: 0.2s;
}

.opened {
  left: 0;
}

.closed {
  left: -1000px;
}
</style>
