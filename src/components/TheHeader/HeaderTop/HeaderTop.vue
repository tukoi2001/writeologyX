<template>
  <div class="header__top">
    <div class="header__top-social">
      <a
        v-for="icon in icons"
        :key="icon.id"
        class="header__top-icon"
        :href="icon.target"
        target="_blank"
      >
        <font-icon :name="icon.icon" />
      </a>
    </div>
    <div class="header__top-logo">
      <a href=""><img :src="IMG_URL" /></a>
    </div>
    <HeaderSetting />
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';
import { IMG_URL } from '@/configs/constants';
import HeaderSetting from './HeaderSetting.vue';

type IconSocial = {
  id: string;
  icon: string;
  target: string;
};

export default defineComponent({
  name: 'HeaderTop',
  components: { HeaderSetting },
  setup() {
    const icons = computed<IconSocial[]>(() => [
      {
        id: '1',
        icon: 'mdi-facebook',
        target: 'https://www.facebook.com/',
      },
      {
        id: '2',
        icon: 'mdi-twitter',
        target: 'https://twitter.com/?lang=vi',
      },
      {
        id: '3',
        icon: 'mdi-instagram',
        target: 'https://www.instagram.com/',
      },
      {
        id: '4',
        icon: 'mdi-linkedin',
        target: 'https://www.linkedin.com/',
      },
    ]);

    return {
      icons,
      IMG_URL,
    };
  },
});
</script>

<style lang="scss" scoped>
.header {
  &__top {
    @include flex-box(space-between);
    margin-bottom: 24px;

    &-social {
      @include flex-box();
      gap: 18px;
    }

    &-icon {
      color: $primary;
      text-decoration: none;
    }
  }
}
</style>
