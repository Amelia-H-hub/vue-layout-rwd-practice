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

const downloads = [
  {
    name: '(1) 申請須知',
    notes: null,
    href: 'https://www.dropbox.com/sh/x2nbaddifkju5ig/AAC-ri4UuGQBst3HJzcb_x8Za?dl=0',
  },
  {
    name: '(2) 徵件說明簡報',
    notes: null,
    href: 'https://www.dropbox.com/sh/g225jtj4j68j3fm/AABd_nc7s3SfPGZC7LB2YjMJa?dl=0',
  },
  {
    name: '(3) 計畫書格式及相關附件',
    notes: '含執行承諾書、個資同意書、關係揭露表等',
    href: 'https://www.dropbox.com/sh/vwttq576hrg9z3w/AAD4XGBPgtyIfH7ZojMzs4uPa?dl=0',
  },
  {
    name: '(4) 常見問題',
    notes: null,
    href: 'https://www.dropbox.com/sh/2v9xpw66q6q68q0/AAAf7tuyDdBOAmAqCY8miXo7a?dl=0',
  },
];
</script>

<template>
  <div id="proposals" class="proposalContainer">
    <div class="proposalContainer__title">
      <p class="proposalContainer__title--text">提案與徵件</p>
    </div>
    <div class="proposalContainer__actions">
      <div class="proposalContainer__actions--card">
        <div class="proposalContainer__actions--card--header">
          <p>徵件說明會</p>
          <a href="https://tier.surveycake.biz/s/8R06a" target="blank" rel="noopener noreferrer">
            點此報名
          </a>
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
          <a href="https://tier.surveycake.biz/s/7Rw6n" target="blank" rel="noopener noreferrer">
            點此提案
          </a>
        </div>
        <div class="proposalItem">
          <div class="proposalItem__content">
            <p>提案系統將於 113年3月31日 (五) 15:00 關閉，請把握時間上傳</p>
          </div>
          <div class="proposalItem__image">
            <img src="@/assets/images/插畫_提案.svg" />
          </div>
        </div>
      </div>
    </div>
    <div class="proposalContainer__process">
      <p>徵件流程</p>
      <div class="proposalContainer__process--image">
        <img src="@/assets/images/web_chart.svg" class="proposalContainer__process--image--web" />
        <img src="@/assets/images/mobile_chart.svg" class="proposalContainer__process--image--mobile" />
      </div>
    </div>
    <div class="proposalContainer__reference">
      <p class="proposalContainer__reference--text">徵件須知與計畫書格式</p>
      <div class="downloadsContainer">
        <div v-for="downloadItem in downloads" :key="downloadItem.name" class="downloadsContainer__download">
          <div class="downloadsContainer__download--content">
            <p class="downloadsContainer__download--content--name">{{ downloadItem.name }}</p>
            <p class="downloadsContainer__download--content--notes">{{ downloadItem.notes }}</p>
          </div>
          <a :href="downloadItem.href" target="_blank" rel="noopener noreferrer">
            下載
          </a>
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
  gap: 50px;
  padding: 40px 28px;
  box-sizing: border-box;
  scroll-margin-top: 47px;

  @include mq('tablet') {
    padding-top: 52px;
    padding-bottom: 60px;
    scroll-margin-top: 58px;
  }

  @include mq('desktop') {
    padding-top: 64px;
    padding-bottom: 80px;
    scroll-margin-top: 70px;
  }

  &__title {
    display: flex;
    justify-content: center;
    width: 100%;

    &--text {
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

        a {
          color: $system-green;
          text-decoration: none;
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

  &__process {
    width: 100%;
    max-width: 956px;
    background-color: #ffffff;
    display: flex;
    flex-direction: column;
    padding: 47px 33px 37.5px 40px;
    box-sizing: border-box;

    p {
      font-family: 'CustomJf';
      font-size: 32px;
      line-height: 40px;
    }

    &--image {
      display: flex;
      justify-content: center;
      margin-top: 28px;
      padding-bottom: 50px;
      border-bottom: 1px solid #7fa482;

      &--web {
        display: none;
        width: 100%;

        @include mq('tablet') {
          display: inline-block;
          width: 100%;
        }
      }

      &--mobile {
        display: block;
        width: 100%;

        @include mq('tablet') {
          display: none;
        }
      }
    }
  }

  &__reference {
    width: 100%;
    max-width: 956px;
    background-color: #ffffff;
    display: flex;
    flex-direction: column;
    padding: 47px 33px 37.5px 40px;
    box-sizing: border-box;

    &--text {
      font-family: 'CustomJf';
      font-size: 32px;
      line-height: 40px;
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
  flex-direction: column;
  width: 100%;

  &__content {
    border-bottom: 1px solid #7fa482;
    padding-bottom: 19px;
    width: 100%;

    @include mq('tablet-s') {
      max-width: calc(100% - 170px);
    }

    @include mq('tablet-l') {
      max-width: 200px;
    }
  }

  &__image {
    position: relative;
    display: flex;
    justify-content: end;

    @include mq('tablet-l') {
      position: absolute;
      right: 33px;
      bottom: 37.5px;
    }
  }
}

.downloadsContainer {
  margin-top: 40px;
  display: flex;
  flex-wrap: wrap;
  gap: 36px;

  &__download {
    border-bottom: 1px solid #7fa482;
    padding-bottom: 19px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 20px;
    flex: 1 1 100%;

    @include mq('tablet') {
      flex: 0 1 calc(50% - 18px);
    }

    &--content {
      display: flex;
      flex-direction: column;

      &--name {
        font-family: 'CustomNotoSansTC';
        font-size: $font-size-l;
        line-height: 28px;
        color: #939393;
      }

      &--notes {
        font-family: 'CustomNotoSansTC';
        line-height: 24px;
      }
    }

    a {
      color: $system-green;
      text-decoration: none;
      background: transparent;
      border: 1px solid $system-green;
      border-radius: 25px;
      padding: 14px 32px;
      min-width: 38px;

      &:hover {
        background-color: #4e8960;
        color: #ffffff;
      }
    }
  }
}
</style>
