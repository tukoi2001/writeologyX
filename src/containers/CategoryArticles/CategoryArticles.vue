<template>
  <div class="category-article mb-16">
    <div class="category-article__list">
      <v-btn
        class="category-article__item"
        v-for="category in categories"
        :key="category.id"
        :loading="isLoading"
        :disabled="isDisabled || isLoading"
        color="#f0f0f0"
      >
        {{ category.name }}
      </v-btn>
    </div>
    <v-card class="category-article__card">
      <v-img
        class="align-end text-white"
        height="360"
        :src="newPost.linkImagePost"
        cover
      >
        <p class="sub-title mb-4">{{ newPost.category }}</p>
        <p class="title">{{ newPost.title }}s</p>
      </v-img>
      <div class="overlay"></div>
    </v-card>
  </div>
</template>

<script lang="ts">
import { defineComponent, computed, ref } from 'vue';

type Category = {
  id: string;
  name: string;
};

type CategoryArticle = {
  id: string;
  category: string;
  title: string;
  linkImagePost: string;
};

export default defineComponent({
  name: 'CategoryArticle',
  components: {},
  setup() {
    const isDisabled = ref<boolean>(false);
    const isLoading = ref<boolean>(false);

    const categories = computed<Category[]>(() => [
      {
        id: '1',
        name: 'tips',
      },
      {
        id: '2',
        name: 'resources',
      },
      {
        id: '3',
        name: 'guides',
      },
    ]);

    const newPost = computed<CategoryArticle>(() => ({
      id: '1',
      category: 'tips',
      title: 'How to choose the best management software',
      linkImagePost:
        'https://assets.website-files.com/62abc23e594f83d9d66b136f/62abfe89ab6b229bab1ed420_management-software-featured-blog-writelogy-x-webflow-template.jpg',
    }));

    return { isDisabled, isLoading, categories, newPost };
  },
});
</script>

<style lang="scss" scoped>
.category-article {
  &__list {
    display: flex;
    gap: 12px;
    margin-bottom: 40px;

    .v-btn--variant-elevated {
      box-shadow: none;
    }
  }

  &__item {
    padding: 12px;
  }

  &__card {
    border-radius: 12px;
    position: relative;
  }

  .overlay {
    @include flex-box(center);
    position: absolute;
    left: 0%;
    top: 0%;
    right: 0%;
    bottom: 0%;
    z-index: 1;
    background-image: -webkit-gradient(
      linear,
      left top,
      left bottom,
      color-stop(40%, transparent),
      to(#000)
    );
    background-image: linear-gradient(180deg, transparent 40%, #000);
  }
}

::v-deep {
  .v-responsive__content {
    padding: 0 24px 48px;

    .sub-title,
    .title {
      padding: 0;
    }

    .sub-title {
      @include text-style(18px, 700, 20px, $white);
      text-transform: uppercase;
    }

    .title {
      @include text-style(22px, 700, 28px, $white);
    }
  }
}
</style>
