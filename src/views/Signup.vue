<template>
  <div class="signup">
    <SignupComponent />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { SignupComponent } from '@/components/signup';

@Component({
  components: {
    SignupComponent,
  },
})
export default class Signup extends Vue {}
</script>
