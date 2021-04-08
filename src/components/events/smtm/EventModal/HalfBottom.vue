<template>
  <div class="modal-content-bottom">
    <div class="modal-content-bottom__1won-coupon-container">
      <p>
        <span>송금할</span>
        <span>1원이 없다면?</span>
      </p>
      <button aria-label="1원 쿠폰 받기" @click="getOneWonCoupon">1원 쿠폰</button>
    </div>

    <ul class="modal-content-bottom__announce">
      <li>
        <p>송금 후, 즉시 당첨 확인 가능 & 1원 환불</p>
        <span class="_sub">(카카오페이 플러스 친구 메세지로 안내)</span>
      </li>
      <li>매일 10회 참여 가능 / 매주 경품 변경</li>
      <li class="_with-button">
        <span>카톡 최신버전에서만 참여가능</span>
        <button aria-label="카카오톡 앱 업데이트 하기 버튼" @click="kakaoAppUpdate">
          카톡 업데이트
        </button>
      </li>
    </ul>

    <EventRemittanceButton />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import EventRemittanceButton from './EventRemittanceButton.vue';

@Component({
  components: { EventRemittanceButton },
})
export default class EventModal extends Vue {
  getOneWonCoupon() {
    alert('1원 쿠폰이 발급되었습니다');
  }

  kakaoAppUpdate() {
    alert('카카오톡 앱 업데이트');
  }

  onRemittance() {
    alert('송금하기 기능 오픈');
  }
}
</script>

<style lang="scss" scoped>
$modules: 'modal-content-bottom';
.#{$modules} {
  top: 50%;
  transform: translateY(800px);
  background-image: url('~@/assets/images/event_smtm_modal/bg_modal_bottom.png');

  &__1won-coupon-container,
  &__announce {
    width: 290px;
    margin: 0 auto;
    border-radius: 4px;
    background-color: rgba(31, 20, 20, 0.6);
    box-shadow: inset 4px 4px 4px 4px rgba(0, 0, 0, 0.2),
      inset 00px 0px 1px 0px rgba(184, 133, 75, 0.5);
    border: 1px solid rgba(189, 133, 75, 0.5);
    padding: 10px 14px;
  }

  &__1won-coupon-container {
    margin-top: 20px;
    display: flex;
    justify-content: space-between;
    p span {
      text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
      font-size: 13px;
      &:nth-child(1) {
        color: #f4b461;
        padding-right: 5px;
      }
      &:nth-child(2) {
        color: #ffd8a9;
      }
    }
    button {
      font-size: 0;
      width: 56px;
      height: 23px;
      background-image: url('~@/assets/images/event_smtm_modal/btn_1won_coupon.png');
      background-size: 100% 100%;
    }
  }

  &__announce {
    margin-top: 10px;
    li {
      font-size: 13px;
      color: #f4b461;
      text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
      position: relative;
      padding-left: 10px;

      &:before {
        content: '';
        position: absolute;
        width: 3px;
        height: 3px;
        border-radius: 50%;
        background-color: #f4b461;
        top: 8.5px;
        left: 0;
      }

      span._sub {
        font-size: 12px;
        font-weight: 200;
      }

      &._with-button {
        display: flex;
        justify-content: flex-start;
        align-content: center;

        button {
          width: 76px;
          height: 22px;
          font-size: 0;
          background-image: url('~@/assets/images/event_smtm_modal/btn_update.png');
          background-size: 100% 100%;
          margin-left: 7px;
        }
      }

      & + li {
        margin-top: 9px;
      }
    }
  }
}
</style>
