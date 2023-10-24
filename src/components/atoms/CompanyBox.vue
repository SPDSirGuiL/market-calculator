<script setup lang="ts">
interface CompanyBoxProps {
  active: boolean;
  text: "Grande" | "Médio" | "Pequeno";
}

const props = defineProps<CompanyBoxProps>();
</script>

<template>
  <div :class="`box ${active ? 'active' : 'non-active'}`">
    <div :class="`check ${active && 'active'}`">
      <q-icon name="check" size="1.25rem" />
    </div>
    <q-icon
      :name="props.active ? 'img:/home-active.svg' : 'img:/home.svg'"
      size="4rem"
    />
    <span> {{ props.text }} </span>
  </div>
</template>

<style lang="scss" scoped>
.active {
  border: 4px solid #14aaff;

  color: #14aaff;
}

.non-active {
  border: 4px solid #5f6a6c;

  color: #5f6a6c;
}

.box {
  position: relative;
  width: 150px;
  height: 150px;
  border-radius: 16px;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  cursor: pointer;

  span {
    margin-top: 20px;

    font-family: "Roboto";
    font-size: 1.5rem;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
  }

  .check {
    display: flex;
    align-items: center;
    justify-content: center;

    color: #fff;

    width: 37px;
    height: 30px;

    border-radius: 0px 16px;
    background: #5f6a6c;

    position: absolute;
    right: -2px;
    top: -2px;
  }

  .active {
    background: #14aaff;
  }
}
</style>
