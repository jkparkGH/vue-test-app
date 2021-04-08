<template>
  <section class="title-neon" :class="{ init: init }">
    <div class="blind">
      <span>Drop the money</span>
    </div>
    <div class="title-neon__container">
      <div class="title-neon__spark">
        <img
          class="title-neon__spark-image-a"
          src="@/assets/images/event_smtm/img_spark_a.png"
          alt=""
        />
        <img
          class="title-neon__spark-image-b"
          src="@/assets/images/event_smtm/img_spark_b.png"
          alt=""
        />
        <img
          class="title-neon__spark-image-c"
          src="@/assets/images/event_smtm/img_spark_b.png"
          alt=""
        />
      </div>
      <img
        class="title-neon__drop-the-text"
        src="@/assets/images/event_smtm/title_drop_the_text.png"
        alt=""
      />
      <img
        class="title-neon__drop-the-effect"
        src="@/assets/images/event_smtm/title_drop_the_neon.png"
        alt=""
      />
      <img
        class="title-neon__money-text-o"
        src="@/assets/images/event_smtm/title_drop_the_money_text_o.png"
        alt=""
      />
      <img
        class="title-neon__money-text-others"
        src="@/assets/images/event_smtm/title_drop_the_money_text_others.png"
        alt=""
      />
      <img
        class="title-neon__money-effect"
        src="@/assets/images/event_smtm/title_drop_the_money_neon.png"
        alt=""
      />
      <img
        class="title-neon__subtitle"
        src="@/assets/images/event_smtm/img_subtitle_text.png"
        alt="송금만 해도 현금이 쏟아진다!"
      />
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class TitleNeon extends Vue {
  init = false;

  initNeonTitle() {
    setTimeout(() => {
      this.init = true;
    }, 1200);
  }

  mounted() {
    this.initNeonTitle();
  }
}
</script>

<style lang="scss" scoped>
$modules: 'title-neon';
.#{$modules} {
  width: 100%;
  overflow: visible;

  &__container {
    position: relative;
    width: 300px;
    margin: 25px auto 0;
    padding-bottom: 5px;
    img {
      display: block;
    }
  }

  // Spark
  &__spark {
    position: absolute;
    left: 26px;
    bottom: 122px;
    width: 80px;
    img {
      display: block;
      width: 100%;
    }
  }

  &__spark-image-a,
  &__spark-image-b,
  &__spark-image-c {
    transform: scale(0);
    transform-origin: bottom right;
    transition: transform 0.1s ease-in;
  }

  &__spark-image-b,
  &__spark-image-c {
    position: absolute;
    left: 0;
    bottom: 0;
  }

  &__spark-image-b {
    transition-delay: 0.06s;
  }
  &__spark-image-c {
    transition-delay: 0.12s;
  }

  &.init &__spark-image-a,
  &.init &__spark-image-b,
  &.init &__spark-image-c {
    transform: scale(1);
  }

  // Drop The Money
  &__drop-the-text {
    // layout frame 역할
    position: static;
    width: 100%;
  }

  &__drop-the-effect,
  &__money-text-o,
  &__money-text-others,
  &__money-effect {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
  }
  &__drop-the-effect {
    animation: DropTheNeonEffect 2.4s infinite 0.22s;
  }
  &__money-text-o {
    animation: ONeonEffect 4.8s infinite 0.32s;
  }
  &__money-text-others {
    animation: MoneyNeonEffect 4.8s infinite 0.32s;
  }
  &__money-text-neon {
  }

  // Subtitle
  &__subtitle {
    width: 240px;
    position: absolute;
    left: calc(50% - 120px);
    top: 124px;
  }
}

@keyframes DropTheNeonEffect {
  0% {
    opacity: 1;
  }
  50% {
    opacity: 1;
  }
  75% {
    opacity: 0.78;
  }
  100% {
    opacity: 1;
  }
}

@keyframes MoneyNeonEffect {
  0% {
    opacity: 1;
  }
  25% {
    opacity: 0.6;
  }
  75% {
    opacity: 0.6;
  }
  100% {
    opacity: 1;
  }
}

@keyframes ONeonEffect {
  0% {
    opacity: 1;
  }
  34% {
    opacity: 0.3;
  }
  36% {
    opacity: 1;
  }
  38% {
    opacity: 0.3;
  }
  40% {
    opacity: 1;
  }
  100% {
    opacity: 1;
  }
}
</style>
