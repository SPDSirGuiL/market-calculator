<script setup lang="ts">
import { Title } from "../atoms";
import { FilterButton } from "../molecules";

const emit = defineEmits(["openMenu"]);
</script>

<template>
  <header>
    <FilterButton @click="emit('openMenu')" />
  </header>
</template>

<style lang="scss" scoped></style>
