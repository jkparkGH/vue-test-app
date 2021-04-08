<template>
  <section class="reword-symbol">
    <picture>
      <source srcset="@/assets/images/event_smtm/bg_symbol_g_money.webp" type="image/webp" />
      <img
        class="reword-symbol__symbol-money"
        src="@/assets/images/event_smtm/bg_symbol_g_money.png"
        alt=""
      />
    </picture>

    <div class="reword-symbol__bang-hands-container">
      <img
        class="reword-symbol__bang-hands-image _left"
        src="@/assets/images/event_smtm/img_bang_hand.png"
        alt=""
      />
      <img
        class="reword-symbol__text-reword"
        src="@/assets/images/event_smtm/img_reword_100million.png"
        alt="총 1억원"
      />
      <img
        class="reword-symbol__bang-hands-image _right"
        src="@/assets/images/event_smtm/img_bang_hand.png"
        alt=""
      />
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class RewordSymbol extends Vue {}
</script>

<style lang="scss" scoped>
$modules: 'reword-symbol';
.#{$modules} {
  position: relative;
  width: 100%;
  margin-top: 8px;

  &__symbol-money {
    display: block;
    width: 320px;
    margin: 0 auto;
    animation: bounceSymbol 0.6s infinite;
  }

  &__bang-hands-container {
    display: flex;
    justify-content: center;
    position: absolute;
    bottom: -5px;
    left: 0px;
    width: 100%;
  }

  &__bang-hands-image {
    width: auto;
    height: 40px;
    transition: transform 0.1s ease-in;
    &._left {
      padding-top: 15px;
      padding-right: 2px;
      animation: bangHangsTicksLeft 0.6s infinite;
      transform-origin: left bottom;
    }
    &._right {
      padding-top: 2px;
      padding-right: 8px;
      transform: scaleX(-1) translateX(-56px) rotate(10deg);
      animation: bangHangsTicksRight 0.6s infinite;
      transform-origin: left bottom;
    }
  }

  &__text-reword {
    display: block;
    width: 115px;
    animation: bounceTextReword 0.6s infinite;
  }
}

@keyframes bounceSymbol {
  0% {
    transform: translateY(0px);
  }
  24% {
    transform: translateY(0px);
  }
  40% {
    transform: translateY(-3px);
  }
  80% {
    transform: translateY(1px);
  }
  100% {
    transform: translateY(0px);
  }
}

@keyframes bounceTextReword {
  0% {
    transform: scale(1);
  }
  24% {
    transform: scale(1);
  }
  40% {
    transform: scale(1.14);
  }
  80% {
    transform: scale(0.96);
  }
  100% {
    transform: scale(1);
  }
}

@keyframes bangHangsTicksLeft {
  0% {
    transform: rotate(0deg);
  }
  24% {
    transform: rotate(0deg);
  }
  40% {
    transform: rotate(-20deg);
  }
  80% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(0deg);
  }
}

@keyframes bangHangsTicksRight {
  0% {
    transform: scaleX(-1) translateX(-56px) rotate(10deg);
  }
  24% {
    transform: scaleX(-1) translateX(-56px) rotate(10deg);
  }
  40% {
    transform: scaleX(-1) translateX(-56px) rotate(-10deg);
  }
  80% {
    transform: scaleX(-1) translateX(-56px) rotate(10deg);
  }
  100% {
    transform: scaleX(-1) translateX(-56px) rotate(10deg);
  }
}
</style>
