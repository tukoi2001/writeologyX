<template>
  <MasterLayout>
    <RecommendArticle />
  </MasterLayout>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import MasterLayout from '@/layouts/MasterLayout.vue';
import RecommendArticle from './RecommendArticle/RecommendArticle.vue';

export default defineComponent({
  name: 'HomeContainer',
  components: { MasterLayout, RecommendArticle },
  setup() {},
});
</script>

<style lang="scss" scoped></style>
