<template>
  <a class="recommend-article__link" href="">
    <div class="recommend-article__image">
      <img :src="IMG_RECOMMEND" alt="image-recommend" />
      <div class="recommend-article__des">
        <div class="recommend-article__des-tip">Tips</div>
        <div class="recommend-article__des-title">
          5 ways to improve your digital project management
        </div>
        <div class="recommend-article__des-info">
          <div class="recommend-article__des-author">
            <img :src="AUTHOR_IMG" alt="author" />
            John Carter
          </div>
          <div class="recommend-article__des-time">
            <font-icon name="mdi-clock-outline" size="24" />
            June 16, 2022
          </div>
        </div>
      </div>
    </div>
  </a>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IMG_RECOMMEND, AUTHOR_IMG } from '@/configs/constants';

export default defineComponent({
  name: 'RecommendArticleImage',
  components: {},
  setup() {
    return { IMG_RECOMMEND, AUTHOR_IMG };
  },
});
</script>

<style lang="scss" scoped>
.recommend-article {
  &__link {
    &:hover {
      .recommend-article__image {
        transform: scale(0.97);
      }

      .recommend-article__image > img {
        transform: scale(1.12);
      }
    }
  }

  &__image {
    position: relative;
    max-height: 525px;
    border-radius: 12px;
    overflow: hidden;
    transition: all 0.3s ease-in-out;

    & > img {
      width: 100%;
      max-height: 526px;
      object-fit: cover;
      transition: all 0.3s ease-in-out;
    }
  }

  &__des {
    position: absolute;
    bottom: 0;
    left: 0;
    padding: 56px 44px;

    &-tip {
      @include text-style(12px, 700, 14px, $primary);
      display: inline-block;
      padding: 12px;
      text-transform: uppercase;
      background-color: $white;
      border-radius: 6px;
    }

    &-info {
      @include flex-box();
      gap: 16px;
    }

    &-title {
      @include text-style(28px, 700, 40px, $white);
      margin: 20px 0 16px;
    }

    &-author,
    &-time {
      @include flex-box();
      @include text-style(16px, 700, 18px, $white);
      gap: 6px;

      & > img {
        width: 32px;
        height: 32px;
        border-radius: 50%;
      }
    }
  }
}
</style>
