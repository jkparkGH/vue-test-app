<template>
  <div class="event-smtm"></div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class EventSmtm extends Vue {}
</script>

<style lang="scss" scoped>
$modules: "event-smtm";
.#{$modules} {
  width: 100%;
}
</style>
