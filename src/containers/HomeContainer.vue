<template>
  <MasterLayout>
    <RecommendArticle />
    <SubscribePremium />
  </MasterLayout>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import MasterLayout from '@/layouts/MasterLayout.vue';
import RecommendArticle from './RecommendArticle/RecommendArticle.vue';
import SubscribePremium from './SubscribePremium/SubscribePremium.vue';

export default defineComponent({
  name: 'HomeContainer',
  components: { MasterLayout, RecommendArticle, SubscribePremium },
  setup() {},
});
</script>

<style lang="scss" scoped></style>
