<script setup lang="ts"></script>

<template>
  <div id="plans" class="planContainer">
    <img src="@/assets/images/插畫_電線桿.svg" class="utilityPole" />
    <img src="@/assets/images/插畫_小貓.svg" class="cat" />
    <div class="planContainer__title">
      <p>計畫概述</p>
    </div>
    <div class="planContainer__content">
      <div class="planContainer__content--card">
        <p class="planContainer__content--card--title">
          我們正在尋找符合永續、公益、共好之計畫構想，<span>能夠付諸實際行動的地方新能量！</span>
        </p>
        <p>
          國家發展委員會整合各部會地方創生資源，協助地方政府、民間團體、青年團隊等推動地方創生事業，發展地方新經濟，點燃全國地方創生之動能。為加速落實推動地方創生工作，110年起於「前瞻基礎建設計畫」規劃辦理「加速推動地方創生計畫」，透過補助地方政府及民間團體推動創生事業，設置青年培力工作站，建立青年返鄉創生支持系統，並強化城鎮機能及環境整備等地方基礎建設，有助於促進地方產業發展，加速達成地方創生目標。<br />
          <br />
          在前述計畫基礎下，國家發展委員會進一步推動獎勵地方創生青年行動所需資金，並搭配專業輔導培力課程，幫助各地有意投入地方創生行動之青年團隊，將各種具實驗性或創新性的構想付諸行動，期望藉此培育更多種籽人才，蓄積未來地方創生、持續深耕發展的動力。
        </p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.planContainer {
  position: relative;
  width: 100%;
  background-image: url('@/assets/images/web_BG_03.svg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  padding-left: 28px;
  padding-right: 28px;
  padding-top: 40px;
  box-sizing: border-box;
  scroll-margin-top: 47px;

  @include mq('tablet') {
    padding-top: 58px;
    scroll-margin-top: 58px;
  }

  @include mq('desktop') {
    padding-top: 64px;
    scroll-margin-top: 70px;
  }

  &__title {
    position: relative;
    width: 100%;
    text-align: center;
    box-sizing: border-box;
    z-index: 99;

    @include mq('desktop-s') {
      padding-left: calc((461 / 1920) * 100% - 28px);
      text-align: left;
    }

    p {
      position: relative;
      font-family: CustomJf;
      font-size: $font-size-xxl;
      line-height: 51px;
      color: #ffffff;
      padding-bottom: 19px;

      &::after {
        content: '';
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        bottom: 0;
        width: 74.5px;
        height: 2px;
        background-color: #ffffff;

        @include mq('desktop-s') {
          left: 0;
          transform: translateX(0);
        }
      }
    }
  }

  &__content {
    position: relative;
    width: 100%;
    display: flex;
    justify-content: center;
    padding-top: 50px;
    padding-bottom: 80px;
    z-index: 99;

    &--card {
      max-width: 855px;
      min-height: 470px;
      background-color: #ffffff;
      padding: 48px 46px 26px 58px;

      p {
        line-height: 28px;
      }

      &--title {
        font-family: 'CustomNotoSansTC';
        font-size: $font-size-l;
        color: $system-green;
        margin-bottom: 42px;

        span {
          display: inline;

          @include mq('tablet-s') {
            display: block;
          }
        }
      }
    }
  }
}

.utilityPole {
  display: none;

  @include mq('desktop-s') {
    display: block;
    position: absolute;
    top: 146.13px;
    left: calc((325.6 / 1920) * 100% - 28px);
  }
}

.cat {
  display: none;

  @include mq('desktop-s') {
    display: block;
    position: absolute;
    right: calc((370.89 / 1920) * 100% - 28px);
    bottom: 97.91px;
  }
}
</style>
