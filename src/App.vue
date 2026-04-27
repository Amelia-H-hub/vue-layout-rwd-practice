<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import NavBar from '@/components/NavBar.vue';
import News from '@/components/News.vue';
import PlanOverview from '@/components/PlanOverview.vue';
import Proposal from '@/components/Proposal.vue';
import Activities from '@/components/Activities.vue';
import Footer from '@/components/Footer.vue';
import BackToTop from '@/components/BackToTop.vue';

const isScrolled = ref(false);
const handleScroll = () => {
  isScrolled.value = window.scrollY > 34;
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});
onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<template>
  <div class="app">
    <NavBar :isScrolled="isScrolled"></NavBar>
    <News></News>
    <PlanOverview></PlanOverview>
    <Proposal></Proposal>
    <Activities></Activities>
    <Footer></Footer>
    <BackToTop :isScrolled="isScrolled" class="backToTop"></BackToTop>
  </div>
</template>

<style lang="scss" scoped>
.app {
  position: relative;
  width: 100%;
}

.backToTop {
  position: fixed;
  right: 56px;
  bottom: 0px;
  z-index: 99;
}
</style>
