<template>
  <div class="cart-modal">
    <div class="cart-modal__wrapper">
      <div class="cart-modal__wrapper-header">
        <div class="cart-modal__wrapper-title">Your Cart</div>
        <font-icon
          class="cart-modal__wrapper-icon"
          size="30"
          name="mdi-close"
          @click="props.onClose"
        />
      </div>

      <div class="cart-modal__wrapper-empty">
        <div class="cart-modal__wrapper-title">No items found.</div>
        <v-btn
          class="cart-modal__wrapper-button"
          :loading="isLoading"
          :disabled="isDisabled || isLoading"
          color="#131313"
          @click="onSubscribes"
        >
          Subscribe now!
        </v-btn>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, type PropType } from 'vue';

export default defineComponent({
  name: 'CartModal',
  components: {},
  props: {
    onClose: {
      type: Function as PropType<void>,
      required: true,
    },
  },
  setup(props) {
    const searchValue = ref<string>('');
    const isDisabled = ref<boolean>(false);
    const isLoading = ref<boolean>(false);

    const onSubscribes = (): void => {
      //TODO: Handle search value
    };

    return {
      props,
      searchValue,
      isDisabled,
      isLoading,
      onSubscribes,
    };
  },
});
</script>

<style lang="scss" scoped>
.cart-modal {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  width: 100vw;
  height: 100vh;
  background-color: #000000cc;
  z-index: 999;

  &__wrapper {
    position: relative;
    top: 50%;
    left: 50%;
    width: 450px;
    border-color: $grey-1;
    border-radius: 12px;
    background-color: $white;
    transform: translate(-50%, -50%);
    box-shadow: 0 2px 7px 0 rgb(0 0 0 / 6%);

    &-header {
      @include flex-box(space-between);
      padding: 16px 24px;
      border-bottom: 1px solid $grey-1;
    }

    &-title {
      @include heading-text();
    }

    &-button {
      min-height: 56px;
      margin-top: 16px;
      padding: 18px 28px;
      border-radius: 8px;
    }

    &-empty {
      @include flex-box(center);
      flex-direction: column;
      padding: 100px 24px;
    }
  }
}

::v-deep {
  .v-btn__content {
    @include text-style(16px, 700, 20px, $white);
    text-transform: capitalize;
  }
}
</style>
