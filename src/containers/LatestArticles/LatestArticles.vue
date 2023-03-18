<template>
  <div class="latest-articles">
    <h2 class="latest-articles__title mb-6">Latest articles</h2>
    <div class="latest-articles__list">
      <ArticleItem
        v-for="article in articles"
        :key="article.id"
        :item="article"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';
import ArticleItem from './ArticleItem.vue';

type LatestArticles = {
  id: string;
  category: string;
  title: string;
  subtitle: string;
  author: {
    id: string;
    name: string;
    image: string;
  };
  linkImagePost: string;
  createdAt: string;
};

export default defineComponent({
  name: 'LatestArticles',
  components: { ArticleItem },
  setup() {
    const articles = computed<LatestArticles[]>(() => [
      {
        id: '1',
        category: 'tips',
        title: 'How to choose the best management software',
        subtitle:
          'Viverra tristique gravida dolor vel aenean egestas libero enim consequat arcu augue euismod est.',
        author: {
          id: '1',
          name: 'John Carter',
          image:
            'https://assets.website-files.com/62abc23e594f83d9d66b136f/62abc23e594f834a736b14c7_john-carter-team-member-brix-templates-avatar-picture.jpg',
        },
        linkImagePost:
          'https://assets.website-files.com/62abc23e594f83d9d66b136f/62abe99991773809b3eb0313_management-thumbnail-blog-writelogy-x-webflow-template.jpg',
        createdAt: 'June 18, 2022',
      },
      {
        id: '2',
        category: 'resources',
        title: '10 productivity tools that are worth checking out',
        subtitle:
          'Viverra tristique gravida dolor vel aenean egestas libero enim consequat arcu augue euismod est.',
        author: {
          id: '2',
          name: 'Sophie Moore',
          image:
            'https://assets.website-files.com/62abc23e594f83d9d66b136f/62abc23e594f8352b86b1477_sohphie-moore-team-member-brix-templates-avatar-picture.jpg',
        },
        linkImagePost:
          'https://assets.website-files.com/62abc23e594f83d9d66b136f/62abe96825e3ea16e4fbacb5_productivity-apps-thumbnail-blog-writelogy-x-webflow-template.jpeg',
        createdAt: 'June 18, 2022',
      },
    ]);

    return { articles };
  },
});
</script>

<style lang="scss" scoped>
.latest-articles {
  &__title {
    @include heading-text();
  }

  &__list {
    display: flex;
    flex-direction: column;
    gap: 48px;
  }
}
</style>
