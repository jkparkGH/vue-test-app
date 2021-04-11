<template>
  <section class="toggle-agreement">
    <h2 class="blind">약관 동의</h2>

    <span class="toggle-agreement__title">모든 약관 내용에 동의 합니다</span>

    <label class="toggle-agreement__button-label" for="agreement-button">
      <input
        class="blind"
        id="agreement-button"
        name="agreement"
        type="checkbox"
        v-model="syncedAgreement"
        required
      />
      <div></div>
    </label>
  </section>
</template>

<script lang="ts">
import { Component, PropSync, Vue } from 'vue-property-decorator';

@Component
export default class ToggleAgreement extends Vue {
  @PropSync('agreement', {
    required: true,
    type: Boolean,
  })
  syncedAgreement!: boolean;
}
</script>

<style lang="scss" scoped>
$module: 'toggle-agreement';
.#{$module} {
  display: flex;
  &__title {
    font-size: 12px;
    font-weight: 400;
    height: 20px;
    line-height: 20px;
    color: #555;
    font-weight: 600;
    white-space: nowrap;
  }

  &__button-label {
    margin-left: 84px;
    position: relative;
    display: inline-block;
    cursor: pointer;
    width: 40px;
    height: 20px;
    border-radius: 12px;

    background-color: #f9f9f9;
    box-shadow: inset 1px 1px 5px rgba(0, 0, 0, 0.05), 1px 1px 5px rgba(0, 0, 0, 0.2);

    & > div {
      background-color: #999;
      border-radius: 50%;
      margin: 2px;
      width: 16px;
      height: 16px;
      box-shadow: 1px 1px 5px rgba(255, 255, 255, 0.4);
      transform: translateX(0px);
      transition: transform 0.2s ease-out;
    }

    input[type='checkbox'] {
      bottom: 0;
      left: 20px;
    }

    input[type='checkbox']:checked + div {
      transform: translateX(20px);
      background-color: #ffeb00;
    }
  }
}
</style>
