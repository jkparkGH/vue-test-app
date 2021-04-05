<template>
  <div class="events-container">
    <EventSmtm />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import EventSmtm from "@/components/events/smtm/index.vue";

@Component({
  components: {
    EventSmtm
  }
})
export default class Events extends Vue {}
</script>
