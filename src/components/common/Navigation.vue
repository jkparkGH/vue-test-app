<template>
  <nav class="navigation" v-show="isShowNavigation">
    <div class="navigation__container">
      <h1 class="navigation__home">
        <router-link to="/">HOME</router-link>
      </h1>
      <ul class="navigation__route-list">
        <li
          v-for="(item, index) in routeList"
          :key="'routeList' + index"
          :class="{ on: item.routeName === currentRouteName }"
        >
          <router-link :to="item.path">{{ item.name }}</router-link>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from 'vue-property-decorator';
import { RouteRecord } from 'vue-router';

@Component
export default class Navigation extends Vue {
  routeList = [
    {
      name: 'Event',
      path: '/events/preview/smtm',
      routeName: 'EventSmtm',
    },
    {
      name: 'Signup',
      path: '/signup',
      routeName: 'Signup',
    },
  ];

  currentRouteName = '';

  @Prop({
    required: false,
    type: Boolean,
    default: true,
  })
  readonly isShowNavigation!: boolean;

  @Watch('$route', { immediate: true, deep: true })
  onRouteChanged({ name }: RouteRecord) {
    if (name) {
      this.currentRouteName = name;
    }
  }
}
</script>

<style scoped lang="scss">
$modules: 'navigation';
.#{$modules} {
  height: 50px;
  overflow: hidden;

  &__container {
    position: fixed;
    width: 100%;
    height: 50px;
    top: 0;
    left: 0;
    background-color: #fff;
    border-bottom: 1px solid #e1e1e1;
    z-index: 3;
    &:after {
      content: '';
      display: table;
      clear: both;
    }
  }

  &__home {
    width: 40px;
    display: inline-block;
    text-align: center;
    box-sizing: content-box;
    a {
      display: inline-block;
      color: #0e0e0e;
      font-size: 14px;
      padding: 14.5px 10px;
    }
  }

  &__route-list {
    float: right;
    padding-right: 10px;
    @media (max-width: 320px) {
      padding-right: 0;
    }
    &:after {
      content: '';
      display: table;
      clear: both;
    }
    li {
      float: left;
      position: relative;
      &.on:after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        border-radius: 4px;
        width: 100%;
        height: 4px;
        background-color: #efefef;
      }
      a {
        color: #0e0e0e;
        padding: 14.5px 10px;
        display: inline-block;
        font-size: 14px;
        font-weight: 600;
      }
    }
  }
}
</style>
