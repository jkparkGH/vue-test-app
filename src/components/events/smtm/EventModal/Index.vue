<template>
  <section class="event-modal" :class="{ 'is-show': syncedShowModal }">
    <HalfTop class="event-modal__half-top" :is-show-modal.sync="syncedShowModal" />
    <HalfBottom class="event-modal__half-bottom" />
  </section>
</template>

<script lang="ts">
import { Component, Vue, PropSync } from 'vue-property-decorator';
import { HalfTop, HalfBottom } from '@/components/events/smtm/EventModal';

@Component({
  components: {
    HalfTop,
    HalfBottom,
  },
})
export default class EventModal extends Vue {
  @PropSync('isShowModal', {
    required: true,
    type: Boolean,
  })
  syncedShowModal!: boolean;

  closeModal() {
    this.syncedShowModal = false;
  }

  getOneWonCoupon() {
    alert('1원 쿠폰이 발급되었습니다');
  }

  kakaoAppUpdate() {
    alert('카카오톡 앱 업데이트 마켓 바로가기');
  }
}
</script>

<style lang="scss" scoped>
$modules: 'event-modal';
.#{$modules} {
  position: static;

  // modal dim
  &:before {
    content: '';
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0;
    transition: opacity 0.2s ease-out;
    background-color: rgba(0, 0, 0, 1);
    transition-delay: 0.1s;
    z-index: -1;
  }

  &__half-top,
  &__half-bottom {
    position: fixed;
    width: 100%;
    height: 50%;
    left: 0;
    z-index: 4;
    transition: transform 0.42s;
    transition-timing-function: cubic-bezier(1, 0, 0.43, 1.12);
    background-size: 100% 100%;
  }

  &__half-bottom {
    top: 50%;
    transform: translateY(800px);
    background-image: url('~@/assets/images/event_smtm_modal/bg_modal_bottom.png');
  }

  &.is-show {
    &:before {
      z-index: 0;
      opacity: 1;
    }
  }

  &.is-show &__half-top {
    animation: showModalAnimation 0.42s 1;
    transform: translateY(0px);
  }
  &.is-show &__half-bottom {
    animation: showModalBottomAnimation 0.42s 1;
    transform: translateY(0px);
  }
}

.is-desktop .event-modal {
  &__half-top,
  &__half-bottom {
    position: absolute;
  }
}

@keyframes showModalAnimation {
  0% {
    transform: translateY(-800px);
  }
  40% {
    transform: translateY(0px);
  }
  60% {
    transform: translateY(-50px);
  }
  70% {
    transform: translateY(0px);
  }
  85% {
    transform: translateY(-10px);
  }
  100% {
    transform: translateY(0px);
  }
}

@keyframes showModalBottomAnimation {
  0% {
    transform: translateY(800px);
  }
  40% {
    transform: translateY(0px);
  }
  60% {
    transform: translateY(50px);
  }
  70% {
    transform: translateY(0px);
  }
  85% {
    transform: translateY(30px);
  }
  100% {
    transform: translateY(0px);
  }
}
</style>
