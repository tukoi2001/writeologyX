<template>
  <div class="the-articles container-default">
    <v-container class="pa-0">
      <v-row justify="space-between">
        <v-col cols="8" class="pa-0 pr-10">
          <LatestArticles />
        </v-col>
        <v-col cols="4" class="pa-0 pl-10">
          <SearchArticle />
          <v-divider class="mt-14 mb-14" />
          <CategoryArticles />
          <PopularArticles />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CategoryArticles from '../CategoryArticles/CategoryArticles.vue';
import LatestArticles from '../LatestArticles/LatestArticles.vue';
import PopularArticles from '../PopularArticles/PopularArticles.vue';
import SearchArticle from '../SearchArticle/SearchArticle.vue';

export default defineComponent({
  name: 'TheArticles',
  components: {
    LatestArticles,
    PopularArticles,
    SearchArticle,
    CategoryArticles,
  },
  setup() {},
});
</script>

<style lang="scss" scoped>
.the-articles {
  padding-top: 50px;
  padding-bottom: 170px;
}
</style>
