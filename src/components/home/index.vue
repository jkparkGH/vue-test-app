<template>
  <div class="main-container">
    <h1>Welcome :D</h1>
    <h3>
      <span>Admin</span>
      <br />
      Sample
      <br />
      Page
      <br />
      <img src="@/assets/images/icon.png" alt="" />
    </h3>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class HomeComponent extends Vue {}
</script>

<style lang="scss" scoped>
$modules: 'main-container';
.main-container {
  padding: 100px;
  @media (max-width: 480px) {
    padding: 48px 24px;
  }
  h1 {
    padding-bottom: 16px;
  }
  img {
    padding-top: 10px;
  }
}
</style>
