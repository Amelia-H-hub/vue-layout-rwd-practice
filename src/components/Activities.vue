<script setup lang="ts">
import { ref, onMounted } from 'vue';
import type { CSSProperties } from 'vue';
import axios from 'axios';

interface NewsItem {
  id: string;
  categoryId: number;
  categoryName: string;
  publishDate: string;
  title: string;
  imageFileName: string;
}

const activities = ref<NewsItem[]>([]);

const getCategoryStyle = (categoryId: number): CSSProperties => {
  let color = '#333333';

  const styleMap: Record<number, string> = {
    1: '#9A2D31',
    2: '#669625',
    3: '#297EA7',
    4: '#7A58A2',
    5: '#8D5E2F',
    6: '#C6790D',
  };

  color = styleMap[categoryId] || '#333333';

  return {
    color: color,
    borderColor: color,
    borderStyle: 'solid',
    borderWidth: '1px',
    borderRadius: '18px',
    width: '116px',
    height: '36px',
    display: 'flex',
    justifyContent: 'center',
    alignItems: 'center',
    marginRight: '20px',
  };
};

const getImageUrl = (imageFileName: string) => {
  return new URL(`../assets/images/活動成果照片/${imageFileName}`, import.meta.url).href;
}

onMounted(async () => {
  try {
    const response = await axios.get('/data/活動成果資料.json');
    activities.value = response.data.events;
  } catch (error) {
    console.error("取得活動成果資訊失敗：", error);
  }
})
</script>

<template>
  <div id="activities" class="activitiesContainer">
    <div class="activitiesContainer__title">
      <p class="activitiesContainer__title--text">活動成果</p>
    </div>
    <div class="activitiesContainer__main">
      <div v-for="activity in activities" :key="activity.id" class="activitiesContainer__main--card">
        <div class="activitiesContainer__main--card--header">
          <p :style="getCategoryStyle(activity.categoryId)">{{ activity.categoryName }}</p>
          <span>{{ activity.publishDate }}</span>
        </div>
        <div class="activitiesContainer__main--card--imgWrap">
          <img :src="getImageUrl(activity.imageFileName)" :alt="activity.title" />
        </div>
        <p class="activitiesContainer__main--card--title">{{ activity.title }}</p>
      </div>
    </div>
    <button class="activitiesContainer__moreActivities">更多活動成果 +</button>
  </div>
</template>

<style lang="scss" scoped>
.activitiesContainer {
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
    scroll-margin-top: 58px;
  }

  @include mq('desktop') {
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
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 45px;
    width: 100%;

    @include mq('tablet') {
      width: calc(1245 / 1920 * 100%);
      min-width: 780px;
    }

    @include mq('desktop-l') {
      width: calc(1245 / 1920 * 100%);
      min-width: 1280px;
    }

    &--card {
      background-color: #ffffff;
      flex: 1 1 100%;
      min-width: 385px;

      @include mq('tablet-l') {
        min-width: 0;
        flex: 1 1 calc(50% - 23px);
      }

      @include mq('desktop-l') {
        min-width: 0;
        flex: 1 1 calc(33% - 30px);
      }

      &--header {
        display: flex;
        align-items: center;
        width: 100%;
        min-height: 80px;
        font-family: 'CustomNotoSansTC';
        padding-left: 20px;
        padding-right: 20px;
        box-sizing: border-box;

        span {
          font-size: 20px;
        }
      }

      &--imgWrap {
        width: 100%;
        height: auto;
        overflow: hidden;

        img {
          width: 100%;
          height: 100%;
          object-fit: cover;
          transition: all 0.2s ease-in-out;

          &:hover {
            transform: scale(1.1);
          }
        }
      }

      &--title {
        display: flex;
        align-items: center;
        width: 100%;
        min-height: 80px;
        font-family: 'CustomNotoSansTC';
        padding: 10px 20px;
        box-sizing: border-box;

        &:hover {
          color: $system-green;
          text-decoration: underline;
          cursor: pointer;
        }
      }
    }
  }

  &__moreActivities {
    width: 300px;
    height: 54px;
    background-color: transparent;
    border: 1px solid $system-green;
    color: $system-green;
    padding: 15px 87px;
    transition: all 0.3s;

    &:hover {
      background-color: #4e8960;
      border-color: #4e8960;
      color: #ffffff;
    }
  }
}
</style>