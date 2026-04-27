<script setup lang="ts">
import { ref } from 'vue';

const props = defineProps({
  isScrolled: {
    type: Boolean,
    required: true,
  },
});

const navItmes = [
  { id: 'news', name: '最新消息', href: '#news' },
  { id: 'plans', name: '計畫概述', href: '#plans' },
  { id: 'proposals', name: '提案與徵件', href: '#proposals' },
  { id: 'activities', name: '活動成果', href: '#activities' },
];

const isShowMenu = ref<Boolean>(false);
</script>

<template>
  <div>
    <div class="navContainer">
      <img src="@/assets/images/web_Banner.svg" class="navContainer__webBackground" />
      <img src="@/assets/images/mobile_Banner.svg" class="navContainer__mobileBackground" />
      <nav class="nav" :class="{ nav__scrolled: isScrolled }">
        <div class="nav__websites">
          <a href="https://www.twrr.ndc.gov.tw/index" target="_blank" rel="noopener noreferrer"
            class="nav__websites--revitalization">
            <img src="@/assets/images/logo_地方創生.svg" alt="地方創生" />
          </a>
          <a href="https://www.ndc.gov.tw/" target="_blank" rel="noopener noreferrer" class="nav__websites--council">
            <img src="@/assets/images/logo_國家發展委員會.svg" alt="國家發展委員會" />
          </a>
        </div>
        <div class="nav__paragraph">
          <a v-for="item in navItmes" :key="item.id" :href="item.href">{{ item.name }}</a>
        </div>
        <img @click="isShowMenu = true" class="nav__menuIcon" src="@/assets/icons/icon_選單.svg" />
      </nav>
    </div>
    <div v-show="isShowMenu" class="menuContainer" @touchmove.prevent>
      <button @click="isShowMenu = false" class="menuContainer__closeBtn">
        <img src="@/assets/icons/icon_關閉視窗.svg" />
      </button>
      <div class="menuContainer__menuList">
        <div v-for="item in navItmes" :key="item.id" class="menuContainer__menuList--menuItem">
          <a :href="item.href" @click="isShowMenu = false">{{ item.name }}</a>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use 'sass:color';

.navContainer {
  position: relative;
  overflow: hidden;
  width: 100%;
  min-height: none;

  @include mq('tablet-s') {
    min-height: 560px;
  }

  &__webBackground {
    display: none;

    @include mq('tablet-s') {
      display: block;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      height: 100%;
    }
  }

  &__mobileBackground {
    width: 100%;
    height: auto;
    display: block;

    @include mq('tablet-s') {
      display: none;
    }
  }
}

.nav {
  position: fixed;
  top: 34px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 999;
  width: calc(100% * (1790 / 1920));
  height: 47px;
  background: #ffffff 0% 0% no-repeat padding-box;
  box-shadow: 0px 0px 15px #00000026;
  opacity: 1;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0px 19px 0px 14px;
  box-sizing: border-box;

  @include mq('tablet') {
    height: 58px;
    padding: 0px 30px 0px 23px;
  }

  @include mq('desktop') {
    height: 70px;
    padding: 0px 40px 0px 32px;
  }

  &__scrolled {
    top: 0;
    transform: translateX(-50%);
    width: 100%;
  }

  &__websites {
    display: flex;
    justify-content: start;
    align-items: center;
    gap: 24px;
    height: 100%;

    &--revitalization {
      height: calc((31 / 70) * 100%);

      img {
        height: 100%;
      }
    }

    &--council {
      height: calc((53 / 70) * 100%);

      img {
        height: 100%;
      }
    }
  }

  &__paragraph {
    display: none;
    justify-content: end;
    align-items: center;
    gap: 32px;

    @include mq('desktop-s') {
      display: flex;
    }

    a {
      text-decoration: none;
      text-align: left;
      font-family: CustomNotoSansTC;
      font-size: $font-size-l;
      line-height: 27px;
      letter-spacing: 0px;
      color: $default-color;
      transition: all 0.3s;

      &:hover {
        color: #3d5a3e;
      }
    }
  }

  &__menuIcon {
    display: block;
    height: calc((32 / 47) * 100%);
    width: auto;
    flex-shrink: 0;
    cursor: pointer;

    @include mq('desktop-s') {
      display: none;
    }
  }
}

.menuContainer {
  position: fixed;
  top: 0;
  left: 0;
  background-color: #3a433a;
  opacity: 0.92;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100vw;
  height: 100vh;
  z-index: 999;

  &__closeBtn {
    position: fixed;
    top: 20px;
    right: 20px;
    width: 57px;
    aspect-ratio: 57 /47;
    background-color: #3a433a;
    border: none;
    box-shadow: 0px 0px 15px #00000026;
    display: flex;
    justify-content: center;
    align-items: center;

    img {
      height: 100%;
      width: auto;
    }
  }

  &__menuList {
    margin-top: 60px;
    width: calc((312 / 412) * 100%);

    &--menuItem {
      width: 100%;
      border-bottom: 1px solid #ffffff;
      padding: 35px 0px;
    }

    a {
      color: #ffffff;
      font-family: 'CustomJf';
      font-size: 28px;
      text-decoration: none;
      line-height: 35px;
    }
  }
}
</style>
