<template>
  <div class="header__top-setting">
    <div class="header__top-cart" @click="isShowCartModal = true">
      Cart {{ `(${totalItemCarts})` }}
    </div>
    <div class="header__top-account">
      <font-icon size="24" name="mdi-account-outline" />
      <font-icon class="header__top-account-down" name="mdi-chevron-down" />
      <div class="header__top-account-list">
        <div class="header__top-account-item">Login</div>
        <div class="header__top-account-item">Account</div>
      </div>
    </div>
    <div class="header__top-search" @click="isShowSearchModal = true">
      <font-icon size="24" name="mdi-magnify" />
    </div>
  </div>
  <SearchModal v-if="isShowSearchModal" :on-close="onCloseSearchModal" />
  <CartModal v-if="isShowCartModal" :on-close="onCloseCartModal" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import SearchModal from '@/components/SearchModal/SearchModal.vue';
import CartModal from '@/components/CartModal/CartModal.vue';

export default defineComponent({
  name: 'HeaderSetting',
  components: { SearchModal, CartModal },
  setup() {
    const totalItemCarts = ref<number>(0);
    const isShowSearchModal = ref<boolean>(false);
    const isShowCartModal = ref<boolean>(false);

    const onCloseSearchModal = (): void => {
      isShowSearchModal.value = false;
    };

    const onCloseCartModal = (): void => {
      isShowCartModal.value = false;
    };

    return {
      totalItemCarts,
      isShowSearchModal,
      isShowCartModal,
      onCloseSearchModal,
      onCloseCartModal,
    };
  },
});
</script>

<style lang="scss" scoped>
.header {
  &__top {
    @include flex-box(space-between);
    margin-bottom: 24px;

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
