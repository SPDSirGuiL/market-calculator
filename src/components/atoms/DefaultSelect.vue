<script setup lang="ts"></script>

<template>
  <q-select multiple use-chips borderless rounded />
</template>

<style lang="scss" scoped>
$field-transition: 0.36s cubic-bezier(0.4, 0, 0.2, 1);
$field-transition-label-right-down: 0.396s cubic-bezier(0.4, 0, 0.2, 1);
$field-transition-label-right-up: 0.324s cubic-bezier(0.4, 0, 0.2, 1);

.q-field--borderless {
  padding: 0 12px;
  background: rgba(0, 0, 0, 0.05);
  border-radius: 28px;

  .q-field__label {
    color: currentColor;
  }

  .q-field__shadow {
    opacity: 0.5;
  }

  &:before {
    background: rgba(0, 0, 0, 0.05);
    opacity: 0;
    transition: opacity $field-transition, background $field-transition;
  }

  &:hover:before {
    opacity: 1;
  }

  &:after {
    height: 2px;
    top: auto;
    transform-origin: center bottom;
    transform: scale3d(0, 1, 1);
    background: currentColor;
    transition: transform $field-transition;
  }
}
</style>
