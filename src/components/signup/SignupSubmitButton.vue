<template>
  <section class="signup-submit-button">
    <button aria-label="가입하기">가입하기</button>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class SignupSubmitButton extends Vue {}
</script>

<style lang="scss" scoped>
$module: 'signup-submit-button';
.#{$module} {
  padding-top: 36px;
  @media (max-width: 480px) {
    padding-top: 16px;
  }
  button {
    width: 120px;
    @media (max-width: 480px) {
      width: 100%;
    }

    font-size: 16px;
    color: #555;
    background-color: #ffeb00;
    border: 2px solid #ffeb00;
    border-radius: 6px;
    padding: 12px 10px;
    font-weight: 600;
    box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.1);
    white-space: nowrap;
  }
}
</style>
