<script setup lang="ts">
import { ref } from "vue";
import { DefaultInput, DefaultSelect } from "../atoms";

const emit = defineEmits(["openNotification"]);

const group = ref(["op1"]);

const options = [
  {
    label: "Option 1",
    value: "op1",
  },
  {
    label: "Option 2",
    value: "op2",
  },
  {
    label: "Option 3",
    value: "op3",
  },
];

const openNotification = () => {
  emit("openNotification");
};
</script>

<template>
  <main class="main-drawer">
    <div class="cnaes">
      <DefaultInput placeholder="Buscar setor pelo nome ou CNAE" />

      <q-option-group
        v-model="group"
        :options="options"
        color="primary"
        type="checkbox"
        class="checkboxes"
      />
    </div>
    <q-separator />

    <div class="locale">
      <div class="badges">
        <q-badge class="state-badge">
          <span>São Paulo</span>
          <div class="button">
            <q-icon name="close" />
          </div>
        </q-badge>
      </div>

      <DefaultSelect class="state-select" label="Selecione o estado" />

      <span class="link" @click="openNotification">
        <q-icon name="img:/pinn.svg" class="icon" />
        Detectar minha localização
      </span>
    </div>
  </main>
</template>

<style lang="scss" scoped>
.main-drawer {
  .cnaes {
    display: flex;
    flex-direction: column;

    justify-content: center;

    padding: 20px;

    .checkboxes {
      margin-top: 20px;

      height: 232px;
    }
  }

  .locale {
    display: flex;
    flex-direction: column;

    justify-content: center;

    padding: 20px;

    .badges {
      display: flex;

      gap: 10px;

      .state-badge {
        display: flex;
        align-items: center;
        justify-content: center;

        gap: 10px;

        border-radius: 16px;
        background: #d9d9d9;
        padding: 6px 10px 5px 10px;

        color: #5f6a6c;

        span {
          font-size: 0.75rem;
        }

        .button {
          background: #ffffff;

          font-size: 0.8125rem;

          padding: 0px;

          border-radius: 50%;

          cursor: pointer;
        }
      }
    }

    .state-select {
      margin-top: 20px;
    }

    .link {
      display: flex;
      align-items: center;

      gap: 10px;

      color: #14aaff;
      font-family: "Roboto";
      font-size: 1.125rem;
      font-style: normal;
      font-weight: 400;
      line-height: normal;

      margin-top: 10px;

      cursor: pointer;

      .icon {
        font-size: 1.25rem;
      }
    }
  }
}
</style>
