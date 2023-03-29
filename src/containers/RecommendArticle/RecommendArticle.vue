<template>
  <div class="recommend-article container-default">
    <v-container class="pa-0">
      <v-row align="center" class="recommend-article__row">
        <v-col cols="8" class="pa-0 pr-5">
          <RecommendArticleImage />
        </v-col>
        <v-col cols="4" class="pa-0 pl-5">
          <div class="recommend-article__relation">
            <div
              v-for="article in articles"
              :key="article.id"
              class="recommend-article__relation-item"
            >
              <div class="recommend-article__relation-category">
                {{ article.category }}
              </div>
              <div class="recommend-article__relation-title">
                {{ article.title }}
              </div>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';
import RecommendArticleImage from './RecommendArticleImage.vue';

type ArticleRelation = {
  id: string;
  title: string;
  link: string;
  category: string;
};

export default defineComponent({
  name: 'RecommendArticle',
  components: { RecommendArticleImage },
  setup() {
    const articles = computed<ArticleRelation[]>(() => [
      {
        id: '1',
        title: 'How to choose the best management software',
        link: '', // TODO: add link
        category: 'tips',
      },
      {
        id: '2',
        title: '3 tips to avoid Internet distractions at work',
        link: '', // TODO: add link
        category: 'tips',
      },
      {
        id: '3',
        title: '7 great productivity apps for your new iPad',
        link: '', // TODO: add link
        category: 'resources',
      },
    ]);

    return { articles };
  },
});
</script>

<style lang="scss" scoped>
.recommend-article {
  padding-top: 60px;
  padding-bottom: 50px;

  &__relation {
    &-item {
      padding: 40px 10px;
      cursor: pointer;
      transition: all 0.3s ease-in;

      &:hover {
        transform: translateX(10px);
      }

      &:not(:last-child) {
        border-bottom: 1px solid $grey-1;
      }
    }

    &-category {
      @include text-style(18px, 700, 20px, $secondary);
      text-transform: uppercase;
      margin-bottom: 12px;
    }

    &-title {
      @include text-style(24px, 700, 34px, $primary);
    }
  }
}
</style>
