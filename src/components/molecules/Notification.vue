<script setup lang="ts"></script>

<template>
  <div class="notification-card">
    <div class="rounded-img">
      <q-img src="../../assets/pin.svg" />
    </div>

    <div class="content-card">
      <q-icon
        name="close"
        size="1.25rem"
        class="close-btn"
        v-close-popup
        data-cy="close-notification"
      />
      <span>
        <slot />
      </span>
    </div>

    <div class="footer-notification">
      <div class="primary-button">Não</div>
      <div class="primary-button">Sim</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.notification-card {
  margin-bottom: 50px;

  display: flex;
  flex-direction: column;
  align-items: center;

  background: transparent;

  width: 310px;

  position: relative;

  .rounded-img {
    z-index: 999;

    position: absolute;
    top: 0;

    display: flex;
    align-items: center;
    justify-content: center;

    background: #fff;

    width: 100px;
    height: 100px;

    padding: 24px;

    border-radius: 50%;
    box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);
  }

  .content-card {
    position: relative;

    border-radius: 16px 16px 0 0;
    background: #fff;

    display: flex;
    flex-direction: column;
    align-items: center;

    margin-top: 50px;

    padding: 55px 20px 25px 20px;

    span {
      color: #5f6a6c;
      text-align: center;
      font-family: "Roboto";
      font-size: 1.125rem;
      font-style: normal;
      font-weight: 400;
      line-height: normal;
    }

    .close-btn {
      color: #4c525a;

      position: absolute;

      right: 16px;
      top: 16px;

      cursor: pointer;
    }
  }

  .footer-notification {
    display: grid;
    grid-template-columns: 1fr 1fr;

    background: #fff;

    width: 100%;

    border-radius: 0px 0px 18px 18px;

    border-top: 1px solid #5f6a6c;

    div {
      width: 100%;
      height: 52px;

      cursor: pointer;

      display: flex;
      align-items: center;
      justify-content: center;

      font-family: "Roboto";
      text-align: center;
      font-size: 1.125rem;
      font-style: normal;
      font-weight: 400;
      line-height: normal;

      &:first-child {
        border-radius: 0px 0px 0px 16px;
        background: #fff;

        color: #5f6a6c;
      }

      &:last-child {
        border-radius: 0px 0px 16px 0px;
        background: #14aaff;

        color: #fff;

        border-left: 1px solid #5f6a6c;
      }
    }
  }
}
</style>
