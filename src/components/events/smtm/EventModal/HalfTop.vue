<template>
  <div class="modal-content-top">
    <button
      class="modal-content-top__button-close"
      aria-label="이벤트 송금하기 모달 닫기 버튼"
      @click="closeModal"
    >
      닫기
    </button>
    <img
      class="modal-content-top__symbol"
      src="@/assets/images/event_smtm_modal/img_modal_symbol.png"
      alt=""
    />
    <img
      class="modal-content-top__title"
      src="@/assets/images/event_smtm_modal/img_modal_title_text.png"
      alt="이벤트 계좌로 1원 보내봐!"
    />
  </div>
</template>

<script lang="ts">
import { Component, Vue, PropSync } from 'vue-property-decorator';

@Component
export default class HalfTop extends Vue {
  @PropSync('isShowModal', {
    required: true,
    type: Boolean,
  })
  syncedShowModal!: boolean;

  closeModal() {
    this.syncedShowModal = false;
  }
}
</script>

<style lang="scss" scoped>
$modules: 'modal-content-top';
.#{$modules} {
  // half top & bottom 공통부분
  & {
    position: fixed;
    width: 100%;
    height: 50%;
    left: 0;
    z-index: 4;
    transition: transform 0.42s;
    transition-timing-function: cubic-bezier(1, 0, 0.43, 1.12);
    background-size: 100% 100%;
  }

  bottom: 50%;
  transform: translateY(-800px);
  background-image: url('~@/assets/images/event_smtm_modal/bg_modal_top.png');
  display: flex;
  justify-content: flex-end;
  flex-direction: column;
  align-content: center;

  // img_chain
  &:before {
    content: '';
    position: absolute;
    top: -50px;
    left: 0;
    width: 110px;
    height: 210px;
    background-image: url('~@/assets/images/event_smtm_modal/img_chain.png');
    background-size: 100% 100%;
    background-repeat: no-repeat;
  }

  &__button-close {
    position: absolute;
    top: 20px;
    right: 20px;
    width: 32px;
    height: 32px;
    font-size: 0px;
    background-image: url('~@/assets/images/event_smtm_modal/btn_close_modal.png');
    background-size: 100% 100%;
    background-repeat: no-repeat;
  }

  &__symbol {
    width: 96px;
    align-self: center;
  }

  &__title {
    width: 266px;
    align-self: center;
    padding: 20px 0 30px;
  }
}
</style>
