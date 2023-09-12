<script setup lang="ts">
import { ref } from "vue";
import { ExpansionItem, Title, DefaultInput } from "../atoms";

const locale = ref({
  state: "",
});

const props = defineProps({
  able: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits(["closeMenu"]);
</script>

<template>
  <div
    class="menu"
    :style="`left: 0; top: ${props.able ? '0' : '-100vh'}; transition: .3s`"
  >
    <q-card-section class="card-header">
      <Title style="font-size: 1.8rem">Filtros</Title>
      <q-btn
        icon="close"
        size="1.25rem"
        flat
        no-caps
        rounded
        class="close-btn"
        @click="emit('closeMenu')"
      />
    </q-card-section>

    <q-separator class="q-mb-none" />

    <q-card-section>
      <ExpansionItem defaultOpened icon="place">
        <template v-slot:title> Localização </template>

        <template v-slot:form>
          <span>Estado</span>
          <DefaultInput v-model="locale.state" />
        </template>
      </ExpansionItem>

      <ExpansionItem icon="business">
        <template v-slot:title> Setor e CNAE </template>
      </ExpansionItem>

      <ExpansionItem icon="show_chart">
        <template v-slot:title> Porte da empresa </template>
      </ExpansionItem>
    </q-card-section>
  </div>
</template>

<style lang="scss" scoped>
.menu {
  position: fixed;

  height: 80vh;
  width: 100vw;

  background: #fff;

  border-radius: 0 0 32px 32px;

  z-index: 9999;

  .card-header {
    display: flex;
    align-items: center;
    justify-content: space-between;

    padding: 10px;

    .close-btn {
      display: flex;
      align-items: center;
      justify-content: center;

      color: #5f6a6c;

      padding: 10px;
    }
  }
}
</style>
