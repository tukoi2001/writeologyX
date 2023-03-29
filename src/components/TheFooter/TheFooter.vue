<template>
  <div class="container-default">
    <v-container class="pa-0">
      <div class="footer flex-column">
        <div class="footer__top flex-column">
          <h2 class="footer__top-title mb-4">Subscribe to our newsletter</h2>
          <span class="footer__top-subtitle mb-5"
            >Lorem ipsum dolor sit amet consectetur adipiscing elit phasellus
            amet dui quam vitae quis leo velit aliquam.</span
          >
          <div class="footer__top-email mb-10">
            <v-text-field label="Enter your email address" hide-details />
            <v-btn>Subscribe</v-btn>
          </div>
          <div class="footer__top-icons">
            <a
              v-for="icon in icons"
              :key="icon.id"
              class="footer__top-icon"
              :href="icon.target"
              target="_blank"
            >
              <font-icon :name="icon.icon" />
            </a>
          </div>
        </div>
        <div class="footer__bottom pt-8 pb-8">
          <p>
            Copyright © Writeology X | Designed by
            <a href="https://brixtemplates.com/">BRIX Templates</a> - Powered by
            <a href="https://webflow.com/">Webflow</a>
          </p>
        </div>
      </div>
    </v-container>
  </div>
</template>

<script lang="ts">
import { defineComponent, computed } from 'vue';

type IconSocial = {
  id: string;
  icon: string;
  target: string;
};

export default defineComponent({
  name: 'TheFooter',
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

    return { icons };
  },
});
</script>

<style lang="scss" scoped>
.footer {
  @include flex-box(center, center);
  width: 100%;

  &__top {
    @include flex-box(center, center);
    max-width: 574px;

    padding-top: 72px;
    padding-bottom: 72px;

    &-title {
      @include heading-text();
    }

    &-subtitle {
      @include sub-title-text();
      text-align: center;
    }

    &-email {
      @include flex-box(center, center);
      gap: 16px;
      width: 100%;
    }

    &-icons {
      display: flex;
      gap: 18px;
    }

    &-icon {
      @include icon-color();
    }
  }

  &__bottom {
    width: 100%;
    border-top: 1px solid $grey-1;
    text-align: center;

    p {
      @include sub-title-text();
    }

    a {
      @include text-link();
      text-decoration: underline;
    }
  }
}

::v-deep {
  .footer {
    .v-btn.v-btn--density-default {
      --v-btn-height: 56px;
      background: $primary;
      color: $white;
    }
  }
}
</style>
