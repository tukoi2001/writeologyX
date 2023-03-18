<template>
  <div class="header__top">
    <div class="header__top-social">
      <a
        v-for="icon in icons"
        :key="icon.id"
        class="header__top-icon"
        :href="icon.target"
        target="_blank"
        ><v-icon size="20">{{ icon.icon }}</v-icon></a
      >
    </div>
    <div class="header__top-logo">
      <a href=""><img :src="IMG_URL" /></a>
    </div>
    <div class="header__top-setting">
      <div class="header__top-cart">Cart {{ `(${totalItemCarts})` }}</div>
      <div class="header__top-account">
        <v-icon size="24">mdi-account-outline</v-icon>
        <v-icon class="header__top-account-down" size="20"
          >mdi-chevron-down</v-icon
        >
        <div class="header__top-account-list">
          <div class="header__top-account-item">Login</div>
          <div class="header__top-account-item">Account</div>
        </div>
      </div>
      <div class="header__top-search">
        <v-icon size="24">mdi-magnify</v-icon>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, ref } from 'vue';
import { IMG_URL } from '@/configs/constants';

type IconSocial = {
  id: string;
  icon: string;
  target: string;
};

export default defineComponent({
  name: 'HeaderTop',
  components: {},
  setup() {
    const totalItemCarts = ref<number>(0);
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

    return { icons, totalItemCarts, IMG_URL };
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

    &-setting {
      @include flex-box();
      gap: 14px;
    }

    &-cart {
      @include text-style(16px, 700, 28px, $primary);
      cursor: pointer;
    }

    &-account {
      @include flex-box();
      position: relative;
      gap: 4px;
      cursor: pointer;

      &-list {
        @include flex-box(center, flex-start);
        gap: 18px;
        flex-direction: column;
        position: absolute;
        top: 25px;
        padding: 0 32px;
        height: 0;
        border: 1px solid $grey-1;
        border-radius: 20px;
        background-color: $white;
        box-shadow: 0 2px 12px 0 rgb(0 0 0 / 12%);
        opacity: 0;
        visibility: hidden;
      }

      &-item {
        @include text-style(16px, 400, 20px, $secondary);
        transition: all 0.3s ease-in-out;

        &:hover {
          color: $primary;
        }
      }

      &-down {
        transition: all 0.3s ease-in-out;
      }

      &:hover {
        .header__top-account-list {
          height: auto;
          padding: 28px 32px;
          opacity: 1;
          visibility: visible;
          transition: all 0.3s ease-in-out;
        }

        .header__top-account-down {
          transform: rotate(-180deg);
        }
      }
    }

    &-search {
      cursor: pointer;
    }
  }
}
</style>
