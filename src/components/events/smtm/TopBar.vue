<template>
  <section class="top-bar">
    <img
      class="top-bar__logo"
      src="@/assets/images/event_smtm/logo_pay.png"
      alt="카카오 페이 송금"
    />
    <h2 class="top-bar__title">10주간의 현금스웩</h2>
    <img class="top-bar__smtm-image" src="@/assets/images/event_smtm/img_top_bar_smtm.png" alt="" />
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class TopBar extends Vue {}
</script>

<style lang="scss" scoped>
$modules: 'top-bar';
.#{$modules} {
  position: relative;
  display: flex;
  justify-content: center;
  width: 100%;
  height: 36px;
  overflow: visible;
  background-color: rgba(0, 0, 0, 0.4);
  border-bottom: 1px solid #ae7941;

  &__logo {
    position: absolute;
    top: 12px;
    left: 10px;
    width: auto;
    height: 13px;
  }

  &__title {
    color: #ae7941;
    font-size: 12px;
    font-weight: 400;
    align-self: center;
  }

  &__smtm-image {
    position: absolute;
    top: 0;
    right: 0;
    width: 100px;
    height: auto;
  }
}
</style>
