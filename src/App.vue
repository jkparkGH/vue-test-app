<template>
  <div id="app">
    <Navigation :is-show-navigation="isShowNavigation" />
    <MoveBack :is-show-move-back="!isShowNavigation" />
    <router-view />
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from 'vue-property-decorator';
import { RouteRecord } from 'vue-router';
import Navigation from '@/components/common/Navigation.vue';
import MoveBack from '@/components/common/MoveBackButton.vue';

@Component({
  components: { Navigation, MoveBack },
})
export default class App extends Vue {
  isShowNavigation = true;

  @Watch('$route', { immediate: true, deep: true })
  onRouteChanged({ name }: RouteRecord) {
    this.isShowNavigation = name !== 'EventSmtm';
  }
}
</script>

<style lang="scss">
@import '@/assets/styles';
</style>
