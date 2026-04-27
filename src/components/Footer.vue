<script setup lang="ts">
const footerContent = [
  {
    title: '主辦單位',
    value: '國家發展委員會'
  },
  {
    title: '執行單位',
    value: '財團法人台灣經濟研究院'
  },
  {
    title: '聯絡方式',
    value: 'im.ndc@tier.org.tw'
  },
  {
    title: '聯絡電話',
    value: '0800-668-688'
  }
];
</script>

<template>
  <div class="footerContainer">
    <div class="footerContainer__main">
      <div v-for="item in footerContent" :key="item.value" class="footerContainer__main--content">
        <p class="footerContainer__main--content--title">{{ item.title }}</p>
        <p class="footerContainer__main--content--value">{{ item.value }}</p>
      </div>
    </div>
    <p class="footerContainer__copyright">Copyright © 2023 國家發展委員會. All rights reserved.</p>
    <img src="@/assets/images/插畫_小鳥.svg" class="footerContainer__birdImg">
    <img src="@/assets/images/插畫_小市集.svg" class="footerContainer__marketImg">
  </div>
</template>

<style lang="scss" scoped>
.footerContainer {
  position: relative;
  width: 100%;
  background-color: #628E63;
  font-family: 'CustomNotoSansTC';
  color: #ffffff;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  gap: 133px;
  padding: 78px 33px;
  box-sizing: border-box;

  &__main {
    display: grid;
    grid-template-columns: auto;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 71px;
    width: 100%;
    padding: 0px 60px;
    box-sizing: border-box;

    @include mq('tablet-l') {
      grid-template-columns: repeat(2, auto);
      column-gap: 104px;
      row-gap: 71px;
    }

    @include mq('desktop-l') {
      grid-template-columns: repeat(4, auto);
    }

    &--content {
      display: flex;
      flex-direction: column;
      gap: 21px;
      align-items: start;

      &--title {
        font-size: 24px;
        line-height: 33px;
      }

      &--value {
        font-size: 20px;
        line-height: 27px;
      }
    }
  }

  &__copyright {
    font-size: 20px;
  }

  &__birdImg {
    display: none;

    @include mq('desktop-s') {
      display: block;
      position: absolute;
      top: 37px;
      right: 2.4vw;
      width: calc(250 / 1920 * 100%);
      max-width: 250px;
      height: auto;
    }
  }

  &__marketImg {
    display: none;

    @include mq('desktop-s') {
      display: block;
      position: absolute;
      bottom: 18px;
      left: calc(90 / 1920 * 100%);
      width: calc(212 / 1920 * 100%);
      max-width: 212px;
      height: auto;
    }
  }
}
</style>