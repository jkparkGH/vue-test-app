<template>
  <section class="birthday-info">
    <h2 class="birthday-info__title">생일</h2>

    <select name="birthday-year" required v-model="syncedBirthdayYear">
      <option value="">년도</option>
      <option v-for="year in yearList" :key="'yearList' + year">
        {{ year }}
      </option>
    </select>

    <select name="birthday-month" v-model="syncedBirthdayMonth" required>
      <option value="">월</option>
      <option v-for="month in monthList" :key="'monthList' + month">
        {{ month }}
      </option>
    </select>

    <select name="birthday-day" v-model="syncedBirthdayDay" required>
      <option value="">일</option>
      <option v-for="day in dayList" :key="'dayList' + day">
        {{ day }}
      </option>
    </select>
  </section>
</template>

<script lang="ts">
import { Component, PropSync, Vue, Watch } from 'vue-property-decorator';

@Component
export default class BirthDayInfo extends Vue {
  @PropSync('birthday_year', {
    required: true,
    type: String,
  })
  syncedBirthdayYear!: string;

  @PropSync('birthday_month', {
    required: true,
    type: String,
  })
  syncedBirthdayMonth!: string;

  @PropSync('birthday_day', {
    required: true,
    type: String,
  })
  syncedBirthdayDay!: string;

  get yearList() {
    const result = [];
    for (let init = 1950; init < 2021; init++) {
      result.push(init.toString());
    }
    return result;
  }

  get monthList() {
    const result = [];
    for (let init = 1; init <= 12; init++) {
      result.push(init.toString());
    }
    return result;
  }

  dayList: number[] = [];

  @Watch('syncedBirthdayMonth', { immediate: true })
  watchLastDay() {
    if (this.syncedBirthdayYear && this.syncedBirthdayMonth) {
      const lastDay = new Date(
        Number(this.syncedBirthdayYear),
        Number(this.syncedBirthdayMonth),
        0
      ).getDate();

      this.dayList = [];

      for (let init = 1; init <= lastDay; init++) {
        this.dayList.push(init);
      }
    }
  }
}
</script>

<style lang="scss" scoped>
$module: 'birthday-info';
.#{$module} {
  display: flex;
  &__title {
    font-size: 12px;
    font-weight: 400;
    height: 40px;
    line-height: 40px;
    color: #777;
    min-width: 34px;
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
}
</style>
