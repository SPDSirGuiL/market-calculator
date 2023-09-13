<script setup lang="ts">
const props = defineProps({
  icon: {
    type: String,
    enum: ["place", "business", "show_chart"],
    required: false,
  },
  defaultOpened: {
    type: Boolean,
  },
});
</script>

<template>
  <q-expansion-item :default-opened="defaultOpened">
    <template v-slot:header>
      <q-item-section style="padding: 16px 0 16px 0" avatar>
        <q-icon :name="props.icon" size="2rem" style="color: #4c525a" />
      </q-item-section>

      <q-item-section>
        <span
          style="
            font-size: 1.5rem;
            line-height: 1.5rem;
            color: #4c525a;
            display: flex;
            align-items: flex-start;
          "
        >
          <slot name="title" />
        </span>
      </q-item-section>
    </template>

    <q-card>
      <q-card-section>
        <slot name="form" />
      </q-card-section>
    </q-card>
  </q-expansion-item>
</template>

<style lang="scss" scoped></style>
