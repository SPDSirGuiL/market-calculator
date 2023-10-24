<script setup lang="ts">
const emit = defineEmits(["closeDrawer"]);

const closeDrawer = () => {
  emit("closeDrawer");
};
</script>

<template>
  <header class="drawer-header">
    <h1 class="title">Filtros</h1>

    <q-btn round flat icon="close" class="icon" @click="closeDrawer" />
  </header>
</template>

<style lang="scss" scoped>
.drawer-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px;

  color: #5f6a6c;

  border-bottom: 1px solid #d9d9d9;

  .title {
    font-family: "Roboto";
    font-size: 1.5rem;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
  }

  .icon {
    font-size: 1.2rem;
  }
}
</style>
