<script setup lang="ts">
import { ref } from "vue";
import { ExpansionItem, Title, DefaultInput } from "../atoms";

const locale = ref({
  state: "",
  city: "",
  cep: "",
  distanceRadius: 30,
});

const options = ref([
  { label: "Label 0", value: "Value 0" },
  { label: "Label 1", value: "Value 1" },
  { label: "Label 2", value: "Value 2" },
  { label: "Label 3", value: "Value 3" },
  { label: "Label 4", value: "Value 4" },
  { label: "Label 5", value: "Value 5" },
  { label: "Label 6", value: "Value 6" },
  { label: "Label 7", value: "Value 7" },
  { label: "Label 8", value: "Value 8" },
  { label: "Label 9", value: "Value 9" },
  { label: "Label 10", value: "Value 10" },
  { label: "Label 11", value: "Value 11" },
  { label: "Label 12", value: "Value 12" },
  { label: "Label 13", value: "Value 13" },
  { label: "Label 14", value: "Value 14" },
  { label: "Label 15", value: "Value 15" },
  { label: "Label 16", value: "Value 16" },
  { label: "Label 17", value: "Value 17" },
  { label: "Label 18", value: "Value 18" },
  { label: "Label 19", value: "Value 19" },
  { label: "Label 20", value: "Value 20" },
  { label: "Label 21", value: "Value 21" },
  { label: "Label 22", value: "Value 22" },
  { label: "Label 23", value: "Value 23" },
  { label: "Label 24", value: "Value 24" },
  { label: "Label 25", value: "Value 25" },
  { label: "Label 26", value: "Value 26" },
  { label: "Label 27", value: "Value 27" },
  { label: "Label 28", value: "Value 28" },
  { label: "Label 29", value: "Value 29" },
]);

const cnaes = ref(null);
const scrollTargetRef = ref(null);
const level = ref(null);
const levels = ref([
  {
    label: "Grande",
    value: "high",
  },
  {
    label: "Média",
    value: "medium",
  },
  {
    label: "Pequena",
    value: "small",
  },
]);

const test = ref(false);

const props = defineProps({
  able: {
    type: Boolean,
    default: false,
  },
});

const emit = defineEmits(["closeMenu"]);

const onLoad = (index: number, done: () => void) => {
  if (!test.value) {
    done();
    return;
  }

  const length = options.value.length;

  for (let x = length + 1; x <= length + 11; x++) {
    options.value.push({
      label: `Label ${x}`,
      value: `Value ${x}`,
    });
  }

  done();
};
</script>

<template>
  <div
    class="menu"
    :style="`left: 0; top: ${props.able ? '0' : '-300vh'}; transition: .3s`"
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
          <div class="select-container">
            <span class="select-span">Estado</span>
            <DefaultInput v-model="locale.state" />
          </div>

          <div class="select-container mt-4">
            <span class="select-span">Cidade</span>
            <DefaultInput v-model="locale.city" />
          </div>

          <div class="select-container mt-4">
            <span class="select-span">CEP</span>
            <DefaultInput v-model="locale.cep" />
          </div>

          <div class="select-container mt-4">
            <div class="span-box">
              <span class="select-span"> Raio de distância </span>
              <span class="distance-radius"
                >({{ locale.distanceRadius }}Km)</span
              >
            </div>
            <q-slider
              v-model="locale.distanceRadius"
              :min="0"
              :max="50"
              track-size="10px"
              thumb-size="35px"
              color="primary"
              label
              :label-value="locale.distanceRadius + 'Km'"
            />
          </div>

          <q-separator class="-ml-4 -mr-4 mt-4 -mb-4" />
        </template>
      </ExpansionItem>

      <ExpansionItem icon="business" v-model="test">
        <template v-slot:title> Setor e CNAE </template>

        <template v-slot:form>
          <div class="select-container">
            <q-input
              class="input-rounded"
              borderless
              rounded
              clearable
              placeholder="Pesquise por números de CNAEs ou sua descrição"
            />

            <div style="height: 200px; overflow: scroll" ref="scrollTargetRef">
              <q-infinite-scroll
                @load="onLoad"
                :offset="25"
                :scroll-target="scrollTargetRef"
              >
                <q-field
                  hide-bottom-space
                  borderless
                  item-aligned
                  class="q-pa-none option-group-field"
                >
                  <q-option-group v-model="cnaes" :options="options">
                    <template v-slot:label="opt">
                      <div class="center-full">
                        <span style="font-size: 0.75rem; color: #5f6a6c">
                          {{ opt.label }}
                        </span>
                      </div>
                    </template>
                  </q-option-group>
                </q-field>

                <template v-slot:loading>
                  <div class="row justify-center q-my-md">
                    <q-spinner-dots color="primary" size="40px" />
                  </div>
                </template>
              </q-infinite-scroll>
            </div>
          </div>

          <q-separator class="-ml-4 -mr-4 mt-4 -mb-4" />
        </template>
      </ExpansionItem>

      <ExpansionItem icon="show_chart">
        <template v-slot:title> Porte da empresa </template>

        <template v-slot:form>
          <div class="select-container">
            <span class="select-span">Tamanhos padronizados</span>
            <q-option-group v-model="level" :options="levels">
              <template v-slot:label="opt">
                <div class="center-full">
                  <span style="font-size: 0.875rem; color: #5f6a6c">
                    {{ opt.label }}
                  </span>
                </div>
              </template>
            </q-option-group>
          </div>

          <q-expansion-item
            dense
            dense-toggle
            expand-separator
            label="Busca avançada"
            header-class="text-primary"
            expand-icon-class="text-primary"
            class="mt-4"
          >
            <div class="select-container mt-4">
              <span class="select-span-small">Faixa de funcionários</span>
              <DefaultInput v-model="locale.state" dense />
            </div>

            <div class="select-container mt-4">
              <span class="select-span-small">Faixa de faturamento</span>
              <DefaultInput v-model="locale.city" dense />
            </div>
          </q-expansion-item>
        </template>
      </ExpansionItem>
    </q-card-section>
  </div>
</template>

<style lang="scss" scoped>
.menu {
  position: fixed;

  width: 100vw;
  min-height: 80vh;

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

  .select-container {
    display: flex;
    flex-direction: column;

    gap: 10px;

    padding: 4px;

    .select-span {
      color: #4c525a;
      font-family: Roboto;
      font-size: 1.25rem;
      font-style: normal;
      font-weight: 400;
      line-height: normal;
    }

    .select-span-small {
      color: #4c525a;
      font-family: Roboto;
      font-size: 1rem;
      font-style: normal;
      font-weight: 400;
      line-height: normal;
    }

    .distance-radius {
      color: #4c525a;
      font-family: Roboto;
      font-size: 1rem;
      font-style: normal;
      font-weight: 400;
      line-height: 1.5rem;
    }

    .span-box {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .option-group-field {
      background: white;

      .center-full {
        display: flex;
        align-items: center;
        justify-content: center;
      }
    }

    .select-span-title {
      color: $primary;
      font-family: Roboto;
      font-size: 1rem;
      font-style: normal;
      font-weight: 400;
      line-height: normal;

      cursor: pointer;
    }
  }

  .advanced-search-header {
    color: $primary;
    border-top: 0;
  }

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
}
</style>
