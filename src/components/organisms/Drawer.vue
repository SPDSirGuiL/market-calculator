<script setup lang="ts">
import { ref } from "vue";
import { DrawerHeader, DrawerBody, Notification } from "../molecules";

//@ts-ignore
import { Geocoder } from "https://maps.googleapis.com/maps/api/js?key=AIzaSyBnIHgOkBve4rUNao-bvclXl1VDcCgT5zE";

interface DrawerProps {
  open: boolean;
}

const props = defineProps<DrawerProps>();

const emit = defineEmits(["closeDrawer"]);

const notification = ref(false);

const openNotification = () => {
  notification.value = true;
};

const getUserLocale = async () => {
  const position = navigator.geolocation.getCurrentPosition(
    onSuccessGetUserLocale,
    onFailedGetUserLocale
  );
};

const onSuccessGetUserLocale = async (position: GeolocationPosition) => {
  console.log(position.coords);

  //@ts-ignore
  const geocoder = new google.maps.Geocoder();
  const address = await geocoder.geocode({
    lat: position.coords.latitude,
    lng: position.coords.longitude,
  });

  // Imprima o CEP.
  console.log(address[0].postalCode);
};

const onFailedGetUserLocale = async () => {};

const closeDrawer = () => {
  emit("closeDrawer");
};
</script>

<template>
  <div :class="`drawer-container ${props.open ? 'opened' : 'closed'}`">
    <DrawerHeader @closeDrawer="closeDrawer" />

    <DrawerBody @openNotification="openNotification" />
  </div>

  <q-dialog v-model="notification">
    <Notification @yes="getUserLocale" @no="notification = false">
      Deseja importar sua localização? Ao importar sua localização, economizamos
      seu tempo para fazer a busca
    </Notification>
  </q-dialog>
</template>

<style lang="scss" scoped>
.drawer-container {
  width: 100vw;
  min-height: 100vh;

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
