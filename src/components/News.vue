<script setup lang="ts">
import { ref, onMounted } from 'vue';
import type { CSSProperties } from 'vue';
import axios from 'axios';

interface NewsItem {
  id: string;
  categoryId: string;
  categoryName: string;
  title: string;
  publishDate: string;
  isPinned: boolean;
}

const news = ref<NewsItem[]>([]);

const getCategoryStyle = (categoryId: string): CSSProperties => {
  let color = '#333333';

  const styleMap: Record<string, string> = {
    '01': '#9A2D31',
    '02': '#669625',
    '03': '#297EA7',
    '04': '#7A58A2',
    '05': '#8D5E2F',
    '06': '#C6790D',
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
    marginRight: '16px',
  };
};

onMounted(async () => {
  try {
    const response = await axios.get('/data/最新消息資料.json');
    news.value = response.data.news;
  } catch (error) {
    console.error('取得最新資料失敗', error);
  }
});
</script>

<template>
  <div id="news" class="newsContainer">
    <p class="newsContainer__title">最新消息</p>
    <div class="newsContainer__newsCards">
      <div v-for="item in news" :key="item.id" class="newsContainer__newsCards--card">
        <div class="newsContainer__newsCards--card--top">
          <div class="newsContainer__newsCards--card--top--categoryTime">
            <p :style="getCategoryStyle(item.categoryId)">{{ item.categoryName }}</p>
            <span>{{ item.publishDate }}</span>
          </div>
          <img v-show="item.isPinned" src="@/assets/icons/icon_置頂.svg" />
        </div>
        <p class="newsContainer__newsCards--card--content">{{ item.title }}</p>
      </div>
    </div>
    <button class="newsContainer__moreNews">更多最新消息 +</button>
  </div>
</template>

<style lang="scss" scoped>
.newsContainer {
  width: 100%;
  background-image: url('@/assets/images/web_BG_01.svg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 64px 28px 80px 28px;
  box-sizing: border-box;
  scroll-margin-top: 47px;

  @include mq('tablet') {
    scroll-margin-top: 58px;
  }

  @include mq('desktop') {
    scroll-margin-top: 70px;
  }

  &__title {
    position: relative;
    color: $system-green;
    font-family: CustomJf;
    font-size: $font-size-xxl;
    text-align: center;
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

  &__newsCards {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 43px;
    max-width: 1250px;
    margin-top: 50px;
    margin-bottom: 52px;

    &--card {
      flex: 1 1 100%;

      @include mq('tablet') {
        flex: 1 1 calc(50% - 43px);
      }

      @include mq('desktop') {
        flex: 1 1 calc(33% - 43px);
      }

      display: flex;
      flex-direction: column;
      gap: 30px;
      height: 225px;
      background-color: #ffffff;

      &--top {
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: 100%;
        padding: 20px 24px 0px 22px;
        box-sizing: border-box;

        &--categoryTime {
          display: flex;
          align-items: center;
          flex: 1;

          span {
            font-size: $font-size-l;
          }
        }
      }

      &--content {
        width: 100%;
        padding: 0px 24px;
        box-sizing: border-box;

        &:hover {
          color: $system-green;
          text-decoration: underline;
          cursor: pointer;
        }
      }
    }
  }

  &__moreNews {
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
