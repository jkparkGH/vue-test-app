<template>
  <div class="event-button">
    <div class="event-button__container">
      <button aria-label="송금하기 버튼" @click="onRemittance">
        <img src="@/assets/images/event_smtm_modal/btn_remittance_text.png" alt="송금하기" />
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class EventRemittanceButton extends Vue {
  onRemittance() {
    alert('송금하기 기능 오픈');
  }
}
</script>

<style lang="scss" scoped>
$modules: 'event-button';
.#{$modules} {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  &__container {
    width: 100%;
    position: absolute;
    z-index: 4;
    bottom: 0;
    left: 0;
    padding: 10px;
    display: flex;
    justify-content: center;

    button {
      position: relative;
      display: flex;
      justify-content: center;
      width: 100%;
      height: 60px;
      font-size: 0px;
      background-image: url('~@/assets/images/event_smtm/btn_goldbar_bottom_bg.webp');
      background-size: 100% 100%;
      background-repeat: no-repeat;
      border-radius: 6px;
      overflow: hidden;
      box-shadow: 5px 5px 15px 0px #000000;

      img {
        align-self: center;
        height: 25px;
      }

      &:after {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-image: url('~@/assets/images/event_smtm/btn_goldbar_bottom_effect.png');
        background-size: 100% 100%;
        background-repeat: no-repeat;
      }
    }
  }
}

.no-webp .event-button__container button {
  background-image: url('~@/assets/images/event_smtm/btn_goldbar_bottom_bg.png');
}
</style>
