<template>
  <main class="signup-container">
    <h1 class="signup-container__title">회원가입</h1>
    <form @submit.prevent="submitSignUp">
      <LoginInfo :user-id.sync="userInfo.id" :user-password.sync="userInfo.password" />
      <GenderSelection :user-gender.sync="userInfo.gender" />
      <BirthDayInfo
        :birthday_year.sync="userInfo.birthday.year"
        :birthday_month.sync="userInfo.birthday.month"
        :birthday_day.sync="userInfo.birthday.day"
      />
      <PhoneNumber
        :tel_company_number.sync="userInfo.phone_number.tel_company_number"
        :last_number.sync="userInfo.phone_number.last_number"
        :is-phone-number-confirm.sync="isPhoneNumberConfirm"
      />
      <ToggleAgreement :agreement.sync="userInfo.agreement" />
      <SignupSubmitButton />
    </form>
  </main>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import {
  LoginInfo,
  GenderSelection,
  BirthDayInfo,
  PhoneNumber,
  ToggleAgreement,
  SignupSubmitButton,
} from './';

@Component({
  components: {
    LoginInfo,
    GenderSelection,
    BirthDayInfo,
    PhoneNumber,
    ToggleAgreement,
    SignupSubmitButton,
  },
})
export default class SignupComponent extends Vue {
  userInfo = {
    id: '',
    password: '',
    gender: '',
    birthday: {
      year: '',
      month: '',
      day: '',
    },
    phone_number: {
      tel_company_number: '',
      last_number: '',
    },
    agreement: false,
  };

  isPhoneNumberConfirm = false;

  submitSignUp() {
    // Clinet Validation
    alert('가입하기!');
  }
}
</script>

<style lang="scss" scoped>
$modules: 'signup-container';
.#{$modules} {
  padding: 100px;
  @media (max-width: 480px) {
    padding: 48px 24px 24px;
  }

  &__title {
    font-size: 24px;
    margin-bottom: 48px;
    position: relative;
    color: #555;
    &:after {
      content: '';
      position: absolute;
      left: 0;
      bottom: -5px;
      width: 90px;
      height: 5px;
      border-radius: 4px;
      background-color: #ffeb00;
    }
  }

  section + section {
    margin-top: 36px;
  }
}
</style>
