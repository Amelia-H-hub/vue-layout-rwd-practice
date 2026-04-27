<script setup lang="ts">
const props = defineProps({
  isScrolled: {
    type: Boolean,
    required: true,
  },
});

const backToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  });
};
</script>

<template>
  <button v-show="isScrolled" @click="backToTop" class="toTop">
    <img src="@/assets/images/web_top.svg" />
  </button>
</template>

<style lang="scss" scoped>
.toTop {
  width: 76px;
  height: 82px;
  background-color: #000000A6;
  opacity: 0.5;
  border: none;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>