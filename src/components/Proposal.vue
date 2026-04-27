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
    <div class="proposalContainer__main">
      <div class="actions">
        <div class="actions__card">
          <div class="actions__card--header">
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
        <div class="actions__card">
          <div class="actions__card--header">
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
      <div class="process">
        <p>徵件流程</p>
        <div class="process__image">
          <img src="@/assets/images/web_chart.svg" class="process__image--web" />
          <img src="@/assets/images/mobile_chart.svg" class="process__image--mobile" />
        </div>
      </div>
      <div class="reference">
        <p class="reference__text">徵件須知與計畫書格式</p>
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
      font-size: 28px;
      line-height: 51px;
      color: $system-green;
      padding-bottom: 19px;

      @include mq('tablet') {
        font-size: 34px;
      }

      @include mq('desktop') {
        font-size: $font-size-xxl;
      }

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

  &__main {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 50px;

    @include mq('desktop-s') {
      width: calc(1200 / 1920 * 100%);
      min-width: 950px;
    }
  }
}

.actions {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  margin-top: 50px;
  width: 100%;

  &__card {
    position: relative;
    display: flex;
    flex-direction: column;
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
        font-size: 24px;
        line-height: 40px;

        @include mq('tablet') {
          font-size: 28px;
        }

        @include mq('desktop') {
          font-size: 32px;
        }
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

.process {
  width: 100%;
  background-color: #ffffff;
  display: flex;
  flex-direction: column;
  padding: 47px 33px 37.5px 40px;
  box-sizing: border-box;

  p {
    font-family: 'CustomJf';
    font-size: 32px;
    line-height: 40px;

    @include mq('tablet') {
      font-size: 28px;
    }

    @include mq('desktop') {
      font-size: 32px;
    }
  }

  &__image {
    display: flex;
    justify-content: center;
    margin-top: 28px;
    padding-bottom: 0px;
    border-bottom: none;

    @include mq('tablet') {
      padding-bottom: 53.5px;
      border-bottom: 1px solid #7fa482;
    }

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

.reference {
  width: 100%;
  background-color: #ffffff;
  display: flex;
  flex-direction: column;
  padding: 47px 33px 37.5px 40px;
  box-sizing: border-box;

  &__text {
    font-family: 'CustomJf';
    font-size: 32px;
    line-height: 40px;

    @include mq('tablet') {
      font-size: 28px;
    }

    @include mq('desktop') {
      font-size: 32px;
    }
  }
}

.downloadsContainer {
  margin-top: 40px;
  display: flex;
  flex-wrap: wrap;
  gap: 36px;
  width: 100%;

  &__download {
    border-bottom: 1px solid #7fa482;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 20px;
    flex: 1 1 100%;
    padding: 28px 8px;
    box-sizing: border-box;

    @include mq('tablet') {
      flex: 0 1 calc(50% - 18px);
      flex-wrap: nowrap;
    }

    &--content {
      display: flex;
      flex-direction: column;
      flex: 1 1 auto;
      min-width: 0;

      @include mq('tablet') {
        flex: 0 1 auto;
      }

      &--name {
        font-family: 'CustomNotoSansTC';
        font-size: $font-size-l;
        line-height: 28px;
      }

      &--notes {
        font-family: 'CustomNotoSansTC';
        font-size: 16px;
        line-height: 22px;
        color: #8B8B8B;
      }
    }

    a {
      flex-shrink: 0;
      color: $system-green;
      text-decoration: none;
      background: transparent;
      border: 1px solid $system-green;
      border-radius: 25px;
      padding: 14px 32px;
      width: 38px;
      margin-left: auto;

      &:hover {
        background-color: #4e8960;
        color: #ffffff;
      }
    }
  }
}
</style>
