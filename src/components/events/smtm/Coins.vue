<template>
  <ul class="coins" :class="{ init: init, parallaxable: parallaxable }">
    <li :style="setParallax(0.4)"></li>
    <li :style="setParallax(0.6)"></li>
    <li :style="setParallax(0.2)"></li>
    <li :style="setParallax(0.2)"></li>
    <li :style="setParallax(0.6)"></li>
    <li :style="setParallax(0.4)"></li>
    <li class="_slip-a"></li>
    <li class="_slip-b"></li>
    <li class="_slip-b"></li>
    <li class="_slip-b"></li>
    <li class="_slip-c"></li>
  </ul>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class Coins extends Vue {
  init = false;
  parallaxable = false;
  scrollY = 0;

  initCoins() {
    setTimeout(() => {
      this.init = true;
      this.parallaxable = true;
    }, 500);
  }

  setParallax(pos: number) {
    return this.parallaxable ? { transform: `translateY(${this.scrollY * pos}px)` } : '';
  }

  scrollEvent() {
    const global = window;
    global.addEventListener('scroll', () => {
      this.scrollY = global.scrollY;
    });
  }

  mounted() {
    this.initCoins();
    this.scrollEvent();
  }
}
</script>

<style lang="scss" scoped>
@mixin calcScales($scale, $width: 110px, $height: 120px) {
  width: $scale * $width;
  height: $scale * $height;
}
@mixin setLayout($top) {
  top: $top;
  transform: translateY(-($top + 130px));
}

@mixin setLayoutL($top, $left, $scale: 1) {
  @include calcScales($scale);
  @include setLayout($top);
  left: $left;
}

@mixin setLayoutR($top, $right, $scale: 1) {
  @include calcScales($scale);
  @include setLayout($top);
  right: $right;
}

@mixin setLayoutSlip($top, $left, $scale: 1) {
  @include calcScales($scale);
  left: $left;
  transform: translateY(-($top + 1300px));
}

$modules: 'coins';
.#{$modules} {
  width: 100%;
  position: static;
  top: 0;
  left: 0;

  // Coin Image Container
  li {
    position: absolute;
    width: 110px;
    height: 120px;
    transition: transform 0.3s cubic-bezier(0.28, 0.81, 0.33, 0.98);
    transition-delay: 0.15s;
    opacity: 0;

    // Coin Image
    &:before {
      content: '';
      width: 100%;
      height: 100%;
      position: absolute;
      background-image: url('~@/assets/images/event_smtm/img_coin.png');
      background-size: 100% 100%;
      background-repeat: no-repeat;
      transform-origin: 50% 50%;
    }

    // parallaxable Coins: 1~5
    &:nth-child(1) {
      @include setLayoutL(130px, -60px);
      &:before {
        filter: blur(1.2px);
      }
    }
    &:nth-child(2) {
      @include setLayoutL(320px, -38px, 0.5);
      &:before {
        transform: rotate(70deg) skewX(15deg) translateY(-10px);
      }
    }
    &:nth-child(3) {
      @include setLayoutL(240px, 65px, 0.35);
      &:before {
        transform: scaleX(-1) rotate(-10deg);
      }
      &:after {
        content: '';
        position: absolute;
        top: 36%;
        left: 16%;
        width: 80%;
        height: 100%;
        border-radius: 50%;
        background-color: rgba(0, 0, 0, 0.16);
        transform: skewX(-10deg) rotate(20deg);
        transform-origin: center;
        z-index: -1;
      }
    }
    &:nth-child(4) {
      @include setLayoutR(180px, 5px, 0.5);
      z-index: 2;
      &:after {
        content: '';
        position: absolute;
        top: 36%;
        left: 16%;
        width: 80%;
        height: 100%;
        border-radius: 50%;
        background-color: rgba(0, 0, 0, 0.16);
        transform: scaleX(-1) skewX(-10deg) rotate(20deg);
        transform-origin: center;
        z-index: -1;
      }
    }
    &:nth-child(5) {
      @include setLayoutR(220px, 28px, 0.4);
      &:before {
        transform: scaleX(0.8) rotate(60deg) skew(5deg, 5deg);
      }
    }
    &:nth-child(6) {
      @include setLayoutR(310px, -40px);
      &:before {
        filter: blur(1.4px);
        transform: scaleX(-1) scaleY(0.7) rotate(70deg) skew(15deg, 15deg);
      }
    }

    // Only Animation slip Coins: 7~11
    &:nth-child(7) {
      @include setLayoutSlip(480px, 20%, 4);
      top: calc(100% + 480px);
      &:before {
        filter: blur(5px);
        transform: scaleX(-1) rotate(10deg);
      }
    }
    &:nth-child(8) {
      @include setLayoutSlip(120px, 30%);
      top: calc(100% + 120px);
      z-index: 2;
      &:before {
        transform: scale(0.5) rotate(5deg) skew(5deg, 5deg);
      }
    }
    &:nth-child(9) {
      @include setLayoutSlip(180px, 25%);
      top: calc(100% + 180px);
      &:before {
        transform: scaleX(0.34) scaleY(0.4) rotate(60deg) skew(5deg, 5deg);
      }
    }
    &:nth-child(10) {
      @include setLayoutSlip(220px, 45%, 1.4);
      top: calc(100% + 220px);
      &:before {
        filter: blur(1.4px);
        transform: scaleX(-1) rotate(5deg);
      }
    }
    &:nth-child(11) {
      @include setLayoutSlip(440px, 0%, 3.6);
      top: calc(100% + 440px);
      &:before {
        filter: blur(5px);
        transform: rotate(10deg);
      }
    }
  }

  &.init li {
    transform: translateY(0px);
    opacity: 1;

    &._slip-a {
      transition-duration: 0.4s;
      transition-delay: 0s;
    }

    &._slip-b {
      transition-duration: 0.4s;
      transition-delay: 0.05s;
    }

    &._slip-c {
      transition-duration: 0.4s;
      transition-delay: 0.15s;
    }
  }

  &.parallaxable li {
    transition-delay: 0s;
  }
}
</style>
