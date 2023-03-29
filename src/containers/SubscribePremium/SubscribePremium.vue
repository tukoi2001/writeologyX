<template>
  <div class="subscribe-premium">
    <v-container>
      <div class="subscribe-premium__wrapper">
        <div class="subscribe-premium__title">
          Subscribe to unlock premium content
        </div>
        <div class="subscribe-premium__subtitle">
          Sed at tellus, pharetra lacus, aenean risus non nisl ultricies commodo
          diam aliquet arcu enim eu leo porttitor habitasse adipiscing porttitor
          varius ultricies facilisis viverra lacus neque.
        </div>
        <div class="subscribe-premium__article">
          <v-row>
            <v-col v-for="article in articles" :key="article.id" cols="4">
              <div class="subscribe-premium__article-item">
                <img :src="article.image" :alt="article.title" />
                <div class="subscribe-premium__article-content">
                  <div class="subscribe-premium__article-category">
                    {{ article.category }}
                  </div>
                  <div class="subscribe-premium__article-title">
                    {{ article.title }}
                  </div>
                </div>
              </div>
            </v-col>
          </v-row>
          <div class="subscribe-premium__article-overlay">
            <div class="subscribe-premium__article-unlock" @click="onUnlock">
              <font-icon name="mdi-lock" />
              <span>Unlock content</span>
            </div>
          </div>
        </div>
      </div>
    </v-container>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';

type ArticleSubscribe = {
  id: string;
  title: string;
  image: string;
  category: string;
};

export default defineComponent({
  name: 'SubscribePremium',
  components: {},
  setup() {
    const articles = computed<ArticleSubscribe[]>(() => [
      {
        id: '1',
        title: 'A comprehensive guide on Agile development',
        category: 'tips',
        image:
          'https://assets.website-files.com/62abc23e594f83d9d66b136f/62b277391fbbeb861ecc93ea_agile-development-thumbnail-blog-writelogy-x-webflow-template.jpeg',
      },
      {
        id: '2',
        title: '10 Productivity tools that are worth checking out',
        category: 'tips',
        image:
          'https://assets.website-files.com/62abc23e594f83d9d66b136f/62b27251d79e456ff4bdf62a_productivity-tools-thumbnail-blog-writelogy-x-webflow-template.jpeg',
      },
      {
        id: '3',
        title: 'Top 7 Must have management tools for productivity',
        category: 'resources',
        image:
          'https://assets.website-files.com/62abc23e594f83d9d66b136f/62b2722af2243fa1008554ae_management-tools-thumbnail.jpeg',
      },
    ]);

    const onUnlock = (): void => {
      // TODO: Handle unlock
    };

    return { articles, onUnlock };
  },
});
</script>

<style lang="scss" scoped>
.subscribe-premium {
  padding: 176px 0;
  background-color: $black-1;

  &__wrapper {
    @include flex-box();
    flex-direction: column;
  }

  &__title {
    @include text-style(32px, 700, 42px, $white);
    margin-bottom: 16px;
    text-align: center;
  }

  &__subtitle {
    @include text-style(16px, 400, 28px, $grey-2);
    max-width: 740px;
    margin-bottom: 32px;
    text-align: center;
  }

  &__article {
    position: relative;

    &-item {
      position: relative;
      max-height: 360px;

      & > img {
        width: 100%;
        max-height: 360px;
        border-radius: 12px;
        object-fit: cover;
      }
    }

    &-content {
      position: absolute;
      bottom: 0;
      left: 0;
      padding: 42px 14px;
    }

    &-category {
      @include text-style(16px, 700, 28px, $white);
      margin-bottom: 16px;
      text-transform: uppercase;
    }

    &-title {
      @include text-style(22px, 700, 28px, $white);
    }

    &-overlay {
      @include flex-box(center);
      position: absolute;
      left: 0%;
      top: 0%;
      right: 0%;
      bottom: 0%;
      z-index: 2;
      background-image: linear-gradient(
        180deg,
        rgba(20, 20, 20, 0),
        rgba(20, 20, 20, 0.53) 29%,
        rgba(20, 20, 20, 0.79) 67%,
        #141414 92%
      );
    }

    &-unlock {
      @include flex-box(center);
      gap: 4px;
      padding: 18px 28px;
      border-radius: 8px;
      background-color: $white;
      cursor: pointer;

      & > span {
        @include text-style(16px, 700, 20px, $primary);
      }
    }
  }
}
</style>
