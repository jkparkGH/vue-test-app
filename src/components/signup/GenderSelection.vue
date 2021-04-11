<template>
  <section class="gender-selection">
    <h2 class="blind">성별 선택</h2>

    <div>
      <input
        class="blind"
        type="radio"
        name="user-gender"
        id="gender-male"
        value="male"
        v-model="syncedUserGender"
        required
      />
      <label class="gender-selection__label" for="gender-male">남성</label>
    </div>

    <div>
      <input
        class="blind"
        type="radio"
        name="user-gender"
        id="gender-female"
        value="female"
        v-model="syncedUserGender"
      />
      <label class="gender-selection__label" for="gender-female">여성</label>
    </div>
  </section>
</template>

<script lang="ts">
import { Component, PropSync, Vue } from 'vue-property-decorator';

@Component
export default class GenderSelection extends Vue {
  value: '' | 'male' | 'female' = '';

  @PropSync('user-gender', {
    required: true,
    type: String,
  })
  syncedUserGender!: string;
}
</script>

<style lang="scss" scoped>
$module: 'gender-selection';
.#{$module} {
  display: flex;
  position: relative;

  input[type='radio'].blind {
    position: absolute;
    bottom: 0;
    left: 100px;
  }

  &__label {
    width: 100px;
    height: 40px;
    display: inline-block;
    font-size: 14px;
    line-height: 40px;
    cursor: pointer;
    border: 1px solid #eee;
    text-align: center;
    color: #777;
    background-color: #efefef;

    box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.1);
  }

  input:checked + label {
    color: #555;
    background-color: #ffeb00;
    font-weight: 600;
  }
}
</style>
