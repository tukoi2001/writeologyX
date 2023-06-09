<template>
  <div class="article-item">
    <div class="article-item__image">
      <img :src="props.item.linkImagePost" />
    </div>
    <div class="article-item__content">
      <div class="article-item__content-category mb-4">
        {{ props.item.category }}
      </div>
      <div class="article-item__content-title mb-2">
        {{ props.item.title }}
      </div>
      <div class="article-item__content-subtitle mb-5">
        {{ props.item.subtitle }}
      </div>
      <div class="article-item__content-author">
        <div class="article-item__author">
          <v-avatar size="small" class="mr-2">
            <v-img :src="props.item.author.image" />
          </v-avatar>
          {{ props.item.author.name }}
        </div>
        <div class="article-item__author">
          <font-icon
            class="article-item__date-icon mr-2"
            size="30"
            name="mdi-clock-outline"
          />
          {{ props.item.createdAt }}
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, type PropType } from 'vue';

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
  name: 'ArticleItem',
  components: {},
  props: {
    item: {
      type: Object as PropType<LatestArticles>,
      required: true,
    },
  },
  setup(props) {
    return {
      props,
    };
  },
});
</script>

<style lang="scss" scoped>
.article-item {
  @include flex-box();
  gap: 32px;
  cursor: pointer;

  &__image {
    flex-shrink: 0;
    width: 314px;
    height: 314px;
    border-radius: 12px;
    overflow: hidden;

    img {
      width: 100%;
      height: 314px;
      object-fit: cover;
      border-radius: 12px;
      transition: all 0.3s ease-in-out;
    }
  }

  &__content {
    transition: all 0.3s ease-in-out;

    &-category {
      @include sub-heading-text();
    }

    &-title {
      @include heading-text();
    }

    &-subtitle {
      @include sub-title-text();
    }

    &-author {
      @include flex-box(flex-start, center);
      gap: 30px;
    }
  }

  &__author {
    @include flex-box();
    @include text-style(16px, 700, 18px, $black-1);
  }

  &:hover {
    .article-item {
      &__image {
        img {
          transform: scale(1.04);
        }
      }

      &__content {
        transform: translateX(10px);
      }
    }
  }
}
</style>
