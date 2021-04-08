<template>
  <section class="reword-info">
    <div class="reword-info__date">
      <span>{{ weekCount }}주차</span>
      <span>{{ `${startDate} ~ ${endDate}` }}</span>
    </div>
    <div class="reword-info__container">
      <p class="reword-info__announce">추첨을 통해 카카오머니를 드립니다.</p>
      <ul class="reword-info__price-list">
        <li>
          <div>백만원</div>
          <span>1명</span>
        </li>
        <li>
          <div>1만원</div>
          <span>100명</span>
        </li>
        <li>
          <div>1천원</div>
          <span>1천명</span>
        </li>
        <li>
          <div>1백원</div>
          <span>15만명</span>
        </li>
      </ul>
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class RewordInfo extends Vue {
  weekCount = 1;
  startDate = '6.30';
  endDate = '7.6';
}
</script>

<style lang="scss" scoped>
$modules: 'reword-info';
$brown: #c88640;
$darkBlack: #160d0b;
$brownBorder: #865c31;

.#{$modules} {
  width: 100%;
  position: relative;
  margin-top: 20px;
  padding-top: 12px;

  &__date {
    position: absolute;
    top: 0;
    left: calc(50% - 60px);
    font-size: 12px;
    background-color: $darkBlack;
    border: 1px solid $brownBorder;
    border-radius: 25px;
    padding: 2px 15px 3px;
    span {
      color: $brown;
      &:first-child {
        font-weight: 600;
      }
      &:last-child {
        padding-left: 10px;
        font-weight: 200;
      }
    }
  }

  &__container {
    border: 1px solid $brownBorder;
    border-radius: 6px;
    width: 270px;
    margin: 0 auto;
    padding-top: 20px;
    padding-bottom: 12px;
    background-color: rgba(0, 0, 0, 0.4);
    font-size: 13px;
  }

  &__announce {
    padding-bottom: 8px;
    color: $brown;
    font-weight: 200;
    text-align: center;
    width: calc(100% - 24px);
    margin: 0 auto;
    border-bottom: 1px solid $brownBorder;
  }

  &__price-list {
    display: flex;
    justify-content: center;
    padding-top: 12px;

    li {
      text-align: center;
      padding: 0 6px;
      &:nth-child(1) div {
        background-image: url('~@/assets/images/event_smtm/text_price_first.png');
      }
      &:nth-child(2) div {
        background-image: url('~@/assets/images/event_smtm/text_price_second.png');
      }
      &:nth-child(3) div {
        background-image: url('~@/assets/images/event_smtm/text_price_third.png');
      }
      &:nth-child(4) div {
        background-image: url('~@/assets/images/event_smtm/text_price_fourth.png');
      }
    }

    li div {
      font-size: 0px;
      width: 45px;
      height: 15px;
      background-size: contain;
    }

    li span {
      color: $brown;
      font-weight: 200;
      font-size: 12px;
    }
  }
}
</style>
