<template>
  <section class="link-sns">
    <h2 class="link-sns__title">친구들도 우리와 함께 갑시다.</h2>
    <div class="link-sns__button-container">
      <button
        class="link-sns__button-share"
        @click="onShareButton('kakaotalk')"
        aria-label="카카오톡으로 공유하기"
      >
        카카오톡
      </button>
      <button
        class="link-sns__button-share"
        @click="onShareButton('kakaostory')"
        aria-label="카카오 스토리에 공유하기"
      >
        카카오 스토리
      </button>
      <button
        class="link-sns__button-share"
        @click="onShareButton('facebook')"
        aria-label="페이스북 피드에 공유하기"
      >
        페이스북
      </button>
      <button
        class="link-sns__button-share"
        @click="onShareButton('twitter')"
        aria-label="트위터 피드에 공유하기"
      >
        트위터
      </button>
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class LinkSns extends Vue {
  onShareButton(type: 'kakaotalk' | 'kakaostory' | 'facebook' | 'twitter') {
    const linkUrl = 'https://www.kakaopay.com/';
    switch (type) {
      case 'kakaotalk': {
        // Kakao.Link.sendDefault({ ... })
        alert('카카오톡 공유하기');
        break;
      }
      case 'kakaostory': {
        // Kakao.Story.share({ ... })
        alert('카카오스토리 공유하기');
        break;
      }
      case 'facebook': {
        window.location.href = `https://www.facebook.com/sharer.php?u=${encodeURIComponent(
          linkUrl
        )}`;
        break;
      }
      case 'twitter': {
        window.location.href = `https://twitter.com/intent/tweet?url=${encodeURIComponent(
          linkUrl
        )}`;
        break;
      }
      default:
        break;
    }
  }
}
</script>

<style lang="scss" scoped>
$modules: 'link-sns';
.#{$modules} {
  position: relative;
  width: 100%;
  max-width: 375px;
  margin: 0 auto;
  margin-top: 40px;
  padding-top: 8px;

  &__title {
    position: absolute;
    top: 0;
    left: calc(50% - 90px);
    font-size: 0;
    width: 180px;
    height: 26px;
    background-image: url('~@/assets/images/event_smtm/text_with_us.png');
    background-size: cover;
    background-position: center;
  }

  &__button-container {
    position: relative;
    width: calc(100% - 40px);
    padding: 14px 0;
    margin: 0 auto;
    display: flex;
    justify-content: center;

    &:before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
      background-image: url('~@/assets/images/event_smtm/bg_sns_buttons.png');
      background-size: 100% 100%;
      background-position: center;
    }
  }
  &__title,
  &__button-container:before {
    animation: NeonEffect 4.8s infinite 0.32s;
  }

  &__button-share {
    width: 56px;
    height: 50px;
    font-size: 0px;
    margin: 0 5px;
    position: relative;
    z-index: 1;
    &:nth-child(1) {
      background-image: url('~@/assets/images/event_smtm/btn_sns_kakaotalk.png');
      background-size: 100% 100%;
      background-position: center;
    }
    &:nth-child(2) {
      background-image: url('~@/assets/images/event_smtm/btn_sns_kakaostory.png');
      background-size: 100% 100%;
      background-position: center;
    }
    &:nth-child(3) {
      background-image: url('~@/assets/images/event_smtm/btn_sns_facebook.png');
      background-size: 100% 100%;
      background-position: center;
    }
    &:nth-child(4) {
      background-image: url('~@/assets/images/event_smtm/btn_sns_twitter.png');
      background-size: 100% 100%;
      background-position: center;
    }
  }
}

@keyframes NeonEffect {
  0% {
    opacity: 1;
  }
  70% {
    opacity: 1;
  }
  90% {
    opacity: 0.3;
  }
  92% {
    opacity: 1;
  }
  94% {
    opacity: 0.3;
  }
  96% {
    opacity: 1;
  }
  98% {
    opacity: 0.6;
  }
  100% {
    opacity: 1;
  }
}
</style>
