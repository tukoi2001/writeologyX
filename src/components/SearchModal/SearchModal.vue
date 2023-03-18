<template>
  <div class="search-modal">
    <div class="search-modal__wrapper">
      <font-icon
        class="search-modal__wrapper-icon"
        size="30"
        name="mdi-close"
        @click="props.onClose"
      />
      <div class="search-modal__wrapper-title">Search for articles</div>
      <v-text-field
        v-model="searchValue"
        class="search-modal__wrapper-input"
        placeholder="Search..."
        variant="outlined"
      />
      <v-btn
        class="search-modal__wrapper-button"
        :loading="isLoading"
        :disabled="isDisabled || isLoading"
        color="#131313"
        width="100%"
        @click="onSearch"
      >
        Search
      </v-btn>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, type PropType } from 'vue';

export default defineComponent({
  name: 'SearchModal',
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

    const onSearch = (): void => {
      //TODO: Handle search value
    };

    return {
      props,
      searchValue,
      isDisabled,
      isLoading,
      onSearch,
    };
  },
});
</script>

<style lang="scss" scoped>
.search-modal {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(19, 19, 19, 0.12);
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
    padding: 56px 44px;

    &-icon {
      position: absolute;
      top: 10px;
      right: 10px;
    }

    &-title {
      @include heading-text();
      text-align: center;
      margin-bottom: 24px;
    }

    &-input {
      @include text-style(16px, 400, 18px, $secondary);
      min-height: 54px;
    }

    &-button {
      min-height: 56px;
      padding: 18px 28px;
      border-radius: 8px;
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
