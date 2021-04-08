<template>
  <section class="event-footer">
    <img
      class="event-footer__bg-image"
      src="@/assets/images/event_smtm/bg_bottom_coins.png"
      alt=""
    />
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class EventFooter extends Vue {}
</script>

<style lang="scss" scoped>
$modules: 'event-footer';
.#{$modules} {
  width: 100%;
  margin-top: 24px;
  &__bg-image {
    display: block;
    width: 100%;
  }
}
</style>
