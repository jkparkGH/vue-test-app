<template>
  <section class="main-button">
    <button aria-label="이벤트 참여하기 버튼" @click="openEventModal">
      <img src="@/assets/images/event_smtm/btn_goldbar_bottom_text.png" alt="참여하기" />
    </button>
  </section>
</template>

<script lang="ts">
import { Component, Vue, PropSync } from 'vue-property-decorator';

@Component
export default class MainButton extends Vue {
  @PropSync('isShowModal', {
    required: true,
    type: Boolean,
  })
  syncedShowModal!: boolean;

  openEventModal() {
    this.syncedShowModal = true;
  }
}
</script>

<style lang="scss" scoped>
$modules: 'main-button';
.#{$modules} {
  width: 100%;
  position: fixed;
  z-index: 2;
  bottom: 0;
  left: 0;
  button {
    position: relative;
    display: flex;
    justify-content: center;
    margin: 10px;
    width: calc(100% - 20px);
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

.no-webp .main-button button {
  background-image: url('~@/assets/images/event_smtm/btn_goldbar_bottom_bg.png');
}

.is-desktop .main-button {
  position: absolute;
}
</style>
