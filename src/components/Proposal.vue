<script setup lang="ts">
const schedule = [
  {
    location: '中區',
    time: '3/21 (二) 10:30',
  },
  {
    location: '南區',
    time: '3/22 (三) 14:30',
  },
  {
    location: '北區',
    time: '3/23 (四) 14:30',
  },
  {
    location: '東區',
    time: '3/24 (五) 14:30',
  },
];
</script>

<template>
  <div class="proposalContainer">
    <div class="proposalContainer__title">
      <p>提案與徵件</p>
    </div>
    <div class="proposalContainer__actions">
      <div class="proposalContainer__actions--card">
        <div class="proposalContainer__actions--card--header">
          <p>徵件說明會</p>
          <button>點此報名</button>
        </div>
        <div class="scheduleContainer">
          <div v-for="item in schedule" :key="item.location" class="scheduleContainer__schedule">
            <p class="scheduleContainer__schedule--location">{{ item.location }}</p>
            <p class="scheduleContainer__schedule--time">{{ item.time }}</p>
          </div>
        </div>
      </div>
      <div class="proposalContainer__actions--card">
        <div class="proposalContainer__actions--card--header">
          <p>提案</p>
          <button>點此提案</button>
        </div>
        <div class="proposalItem">
          <div class="proposalItem__content">
            <p>提案系統將於 113年3月31日 (五) 15:00 關閉，請把握時間上傳</p>
            <img src="@/assets/images/插畫_提案.svg" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.proposalContainer {
  width: 100%;
  background-image: url('@/assets/images/web_BG_02.svg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 40px 28px;
  box-sizing: border-box;

  @include mq('tablet') {
    padding-top: 52px;
    padding-bottom: 60px;
  }

  @include mq('desktop') {
    padding-top: 64px;
    padding-bottom: 80px;
  }

  &__title {
    display: flex;
    justify-content: center;
    width: 100%;

    p {
      position: relative;
      font-family: CustomJf;
      font-size: $font-size-xxl;
      line-height: 51px;
      color: $system-green;
      padding-bottom: 19px;

      &::after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 50%;
        transform: translateX(-50%);
        width: 74.5px;
        height: 2px;
        background-color: $system-green;
      }
    }
  }

  &__actions {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    margin-top: 50px;

    &--card {
      position: relative;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 28px;
      background-color: #ffffff;
      padding: 47px 33px 37.5px 40px;
      box-sizing: border-box;
      flex: 1 1 100%;

      @include mq('tablet-l') {
        flex: 1 1 calc(50% - 10px);
      }

      &--header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 100%;

        p {
          font-family: 'CustomJf';
          font-size: 32px;
          line-height: 40px;
        }

        button {
          color: $system-green;
          background: transparent;
          border: 1px solid $system-green;
          border-radius: 25px;
          padding: 14px 32px;

          &:hover {
            background-color: #4e8960;
            color: #ffffff;
          }
        }
      }
    }
  }
}

.scheduleContainer {
  display: flex;
  flex-wrap: wrap;
  gap: 36px;

  &__schedule {
    border-bottom: 1px solid #7fa482;
    padding-bottom: 19px;
    flex: 1 1 100%;

    @include mq('tablet-s') {
      flex: 0 1 calc(50% - 18px);
    }

    &--location {
      font-family: 'CustomNotoSansTC';
      font-size: $font-size-l;
      line-height: 28px;
      color: #939393;
    }

    &--time {
      font-family: 'CustomNotoSansTC';
      line-height: 24px;
    }
  }
}

.proposalItem {
  // position: relative;
  display: flex;
  width: 100%;

  &__content {
    border-bottom: 1px solid #7fa482;
    padding-bottom: 19px;
    max-width: 200px;
  }

  img {
    position: absolute;
    right: 0;
    bottom: 0;
  }
}
</style>
