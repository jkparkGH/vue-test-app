<template>
  <div class="home">
    <MainLanding />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import MainLanding from "@/components/home/index.vue";

@Component({
  components: {
    MainLanding
  }
})
export default class Home extends Vue {}
</script>
