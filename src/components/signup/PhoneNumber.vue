<template>
  <section class="phone-number" style="margin-top: 12px">
    <div class="phone-number__input">
      <h2 class="phone-number__title">연락처</h2>

      <select required v-model="syncedTelCompanyNumber">
        <option value="">선택</option>
        <option v-for="number in telCompanyNumberList" :key="'telCompanyNumberList' + number">
          {{ number }}
        </option>
      </select>

      <input
        type="number"
        placeholder="숫자만 입력해주세요"
        required
        pattern="^([0-9]){7,8}$"
        v-model="syncedLastNumber"
      />

      <button
        class="phone-number__request-comfirm"
        aria-label="휴대번호 인증 번호 요청"
        @click.prevent="requestSms"
      >
        인증
      </button>
    </div>

    <div class="phone-number__confirm" v-show="isShowConfirmUi">
      <span class="phone-number__confirm-timer">남은시간 {{ calcTime }}</span>

      <input type="number" placeholder="숫자만 입력해주세요" pattern="^([0-9]){10,11}$" required />

      <button
        class="phone-number__request-comfirm"
        aria-label="휴대번호 인증번호 확인"
        @click.prevent="confirmPhoneNumber"
      >
        확인
      </button>
    </div>
  </section>
</template>

<script lang="ts">
import { Component, PropSync, Vue } from 'vue-property-decorator';

@Component
export default class PhoneNumber extends Vue {
  telCompanyNumberList = ['010', '011', '016', '017', '018', '019'];
  timer = 0;
  timerStart = false;
  isShowConfirmUi = false;

  currentInterval!: number;

  @PropSync('tel_company_number', {
    required: true,
    type: String,
  })
  syncedTelCompanyNumber!: string;

  @PropSync('last_number', {
    required: true,
    type: String,
  })
  syncedLastNumber!: string;

  @PropSync('isPhoneNumberConfirm', {
    required: true,
    type: Boolean,
  })
  syncedIsPhoneNumberConfirm!: boolean;

  get calcTime() {
    const minute = Math.floor(this.timer / 60).toString();
    const second = (this.timer % 60).toString();

    const setZeroString = (time: string) => {
      return time.length === 1 ? '0' + time : time;
    };

    return `${setZeroString(minute)}:${setZeroString(second)}`;
  }

  startTimer() {
    if (this.timerStart) {
      clearInterval(this.currentInterval);
    }

    this.timer = 120;
    this.timerStart = true;

    this.currentInterval = setInterval(() => {
      if (this.timer === 0) {
        this.timerStart = false;
        clearInterval(this.currentInterval);
        alert('인증 가능 시간이 초과되었습니다, 다시 요청해주세요');
      } else {
        this.timer--;
      }
    }, 1000);
  }

  async requestSms() {
    // Client Validation Phone Number
    if (!this.syncedTelCompanyNumber || this.syncedLastNumber.toString().length < 7) {
      alert('연락처를 입력해주세요');
      return;
    }
    // -> Reqeust API
    // const response = apiServiceCall()
    // -> Response 200
    this.isShowConfirmUi = true;
    this.startTimer();
    alert('인증번호가 전송되었습니다');
  }

  async confirmPhoneNumber() {
    // Request Validation Phone Number API
    // const response = apiServiceCall()
    // -> Response 200
    this.syncedIsPhoneNumberConfirm = true;
    alert('인증번호 확인이 완료되었습니다');
  }
}
</script>

<style lang="scss" scoped>
$module: 'phone-number';
.#{$module} {
  &__title {
    font-size: 12px;
    font-weight: 400;
    height: 40px;
    line-height: 40px;
    color: #777;
    white-space: nowrap;
    min-width: 34px;
  }

  &__input {
    display: flex;
  }

  select {
    margin-left: 8px;
    padding: 10px 0;
    height: 40px;
    border-radius: 4px;
    background-color: #efefef;
    border: 2px solid #efefef;
    &:focus {
      outline: 0;
    }
  }

  input[type='number'] {
    border: 0px;
    border-bottom: 2px solid #aaa;
    display: block;
    width: 120px;
    height: 40px;
    margin: 0 8px;
    &:focus {
      outline: 0;
      border-color: #333;
    }
  }

  &__request-comfirm {
    border: 2px solid #777;
    border-radius: 6px;
    padding: 10px;
    font-weight: 600;
    box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.1);
    white-space: nowrap;

    &:hover {
      box-shadow: inset 1px 1px 5px rgba(0, 0, 0, 0.1);
    }
  }

  &__confirm {
    margin-top: 12px;
    display: flex;

    input[type='number'] {
      margin-left: 20px;
    }

    button {
      color: #555;
      background-color: #ffeb00;
      border: 2px solid #ffeb00;

      &:hover {
        box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.1);
      }
    }
  }

  &__confirm-timer {
    font-size: 12px;
    font-weight: 400;
    height: 40px;
    line-height: 40px;
    color: rgb(200, 70, 70);
    white-space: nowrap;
    min-width: 34px;
  }
}
</style>
