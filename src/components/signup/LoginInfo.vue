<template>
  <section clas="login-info">
    <h2 class="blind">로그인 정보</h2>

    <input
      class="login-info__input"
      v-model="syncedUserId"
      name="user-id"
      type="text"
      placeholder="아이디(영문 숫자 포함 6~12자)"
      :pattern="regExpID"
      title="영문 숫자 포함 6~12자"
      autocomplete
      required
    />

    <input
      class="login-info__input"
      v-model="syncedUserPassword"
      name="user-password"
      type="password"
      placeholder="비밀번호(영문 대소문자 숫자 특수문자 포함 8~16자)"
      :pattern="regExpPassword"
      title="영문 숫자 특수문자 포함 8~16자"
      autocomplete="new-password"
      required
    />

    <!-- <input
      class="login-info__input"
      type="password"
      placeholder="비밀번호 확인"
      :pattern="regExpPassword"
      title="영문 숫자 특수문자 포함 8~16자"
      autocomplete="new-password"
      required
    /> -->
  </section>
</template>

<script lang="ts">
import { Component, PropSync, Vue } from 'vue-property-decorator';

@Component
export default class LoginInfo extends Vue {
  regExpID = '^([A-Za-z0-9_]){6,12}$';
  regExpPassword = '^(?=.*?[A-Z])(?=.*?[a-z])(?=.*?[0-9])(?=.*?[#?!@$%^&*-]).{8,16}$';

  @PropSync('user-id', {
    required: true,
    type: String,
  })
  syncedUserId!: string;

  @PropSync('user-password', {
    required: true,
    type: String,
  })
  syncedUserPassword!: string;
}
</script>

<style lang="scss" scoped>
$module: 'login-info';
.#{$module} {
  &__input {
    border: 0px;
    border-bottom: 2px solid #aaa;
    display: block;
    width: 280px;
    height: 40px;

    &:focus {
      outline: 0;
      border-color: #333;
    }

    & + input {
      margin-top: 10px;
    }
  }
}
</style>
