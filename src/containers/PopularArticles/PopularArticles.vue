<template>
  <div class="popular-articles">
    <div class="popular-articles__title">Popular Articles</div>
    <div class="popular-articles__list">
      <div
        v-for="article in articles"
        :key="article.id"
        class="popular-articles__item"
      >
        <div class="popular-articles__item-image">
          <img :src="article.image" :alt="article.title" />
        </div>
        <div class="popular-articles__item-title">{{ article.title }}</div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';

type PopularArticle = {
  id: string;
  title: string;
  image: string;
};

export default defineComponent({
  name: 'PopularArticles',
  components: {},
  setup() {
    const articles = computed<PopularArticle[]>(() => [
      {
        id: '1',
        title: '10 Best collaboration software for your team',
        image:
          'https://assets.website-files.com/62abc23e594f83d9d66b136f/62abe3a09177383d10eae70a_collaboration-software-thumbnail-blog-writelogy-x-webflow-template-.jpg',
      },
      {
        id: '2',
        title: 'A complete guide to learn project management',
        image:
          'https://assets.website-files.com/62abc23e594f83d9d66b136f/62abe33779b3d5971674d153_project-management-thumbnail-blog-writelogy-x-webflow-template-.jpg',
      },
      {
        id: '3',
        title: 'How time tracking can improve team management',
        image:
          'https://assets.website-files.com/62abc23e594f83d9d66b136f/62abe1c991773849cceae17c_time-tracking-thumbnail-blog-writelogy-x-webflow-template-.jpg',
      },
    ]);

    return { articles };
  },
});
</script>

<style lang="scss" scoped>
.popular-articles {
  &__title {
    @include heading-text();
    margin-bottom: 32px;
  }

  &__list {
    @include flex-box(center, flex-start);
    flex-direction: column;
    gap: 22px;
  }

  &__item {
    @include flex-box();
    gap: 20px;
    cursor: pointer;

    &-image {
      flex-shrink: 0;
      width: 132px;
      height: 132px;
      border-radius: 12px;
      overflow: hidden;

      img {
        width: 132px;
        height: 132px;
        object-fit: cover;
        transition: all 0.3s ease-in-out;
      }
    }

    &-title {
      @include text-style(18px, 700, 28px, $primary);
    }

    &:hover {
      .popular-articles__item-image {
        img {
          transform: scale(1.15);
        }
      }
    }
  }
}
</style>
