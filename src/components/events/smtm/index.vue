<template>
  <main class="event-smtm" :class="{ 'is-desktop': !isMobile, 'no-webp': !isWebpUsable }">
    <h1 class="blind">카카오페이 쇼미더머니6 송금 이벤트</h1>
    <section class="event-smtm__mobile-layout">
      <TopBar />
      <TitleNeon />
      <RewordSymbol />
      <RewordInfo />
      <LinkSns />
      <Coins />
      <MainButton :is-show-modal.sync="isShowModal" />
      <EventModal :is-show-modal.sync="isShowModal" />
      <EventFooter />
    </section>
  </main>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import {
  TopBar,
  TitleNeon,
  RewordSymbol,
  RewordInfo,
  LinkSns,
  MainButton,
  Coins,
  EventFooter,
} from './';
import { EventModal } from './EventModal';

import { checkWebPSupport, deviceMobileCheck, deviceTabletCheck } from '@/utils/functions';

@Component({
  components: {
    TopBar,
    TitleNeon,
    RewordSymbol,
    RewordInfo,
    LinkSns,
    MainButton,
    Coins,
    EventFooter,
    EventModal,
  },
})
export default class EventSmtm extends Vue {
  isMobile = false;
  isShowModal = false;
  isWebpUsable = false;

  setBackgroundBody(isMount: boolean) {
    const bodyEl = document.getElementsByTagName('body')[0];
    bodyEl.style.backgroundColor = isMount ? '#121714' : 'transparent';
  }

  initEventPage() {
    this.isMobile = deviceMobileCheck() || deviceTabletCheck();
    this.isWebpUsable = checkWebPSupport();
    this.setBackgroundBody(true);

    if (!this.isMobile) {
      alert(
        'Chrome DevTools로 모바일 화면을 확인해주세요 \n(Windows) Ctrl + Shift + I 또는 (Mac) Cmd + Opt + I \n375 x 667 해상도(iPhone6/7/8)에 최적화 되어있습니다'
      );
    }
  }

  created() {
    this.initEventPage();
  }

  beforeDestroy() {
    this.setBackgroundBody(false);
  }
}
</script>

<style lang="scss" scoped>
$modules: 'event-smtm';
.#{$modules} {
  width: 100%;
  background-color: #121714;

  &__mobile-layout {
    position: relative;
    width: 100%;
    overflow: hidden;
    margin: 0 auto;
    background-image: url('~@/assets/images/event_smtm/bg_event_main.webp');
    background-size: cover;
    background-attachment: fixed;
  }

  &.is-desktop {
    @media (min-width: 414px) {
      padding: 80px 0;
      .event-smtm__mobile-layout {
        max-width: 414px;
        border: 1px dashed #3d2b17;
        background-size: 414px auto;
        background-position: bottom -160px right 50%;
      }
    }
  }
}

.no-webp .event-smtm__mobile-layout {
  background-image: url('~@/assets/images/event_smtm/bg_event_main.png');
}
</style>
