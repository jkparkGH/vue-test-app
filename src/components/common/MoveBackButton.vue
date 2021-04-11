<template>
  <button class="move-back" v-show="isShowMoveBack" @click="moveBack">←</button>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
@Component
export default class MoveBackButton extends Vue {
  @Prop({
    required: false,
    type: Boolean,
    default: true,
  })
  readonly isShowMoveBack!: boolean;

  moveBack() {
    this.$router.back();
  }
}
</script>

<style scoped lang="scss">
$modules: 'move-back';
.#{$modules} {
  position: fixed;
  z-index: 10;
  bottom: 20px;
  right: 20px;
  width: 24px;
  height: 24px;
  line-height: 16px;
  border-radius: 50%;
  overflow: hidden;
  background-color: #000;
  border: 2px solid #fff;
  color: yellow;
  font-weight: 600;
  color: #fff;

  @media (max-width: 480px) {
    display: none;
  }
}
</style>
