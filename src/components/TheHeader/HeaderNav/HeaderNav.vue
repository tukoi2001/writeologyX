<template>
  <ul class="header__nav">
    <li v-for="route in routerList" :key="route.id" class="header__nav-item">
      <router-link class="header__nav-link" :to="{ name: route.to }">{{
        route.title
      }}</router-link>
      <ul v-if="route.children" class="header__nav-dropdown">
        <li
          v-for="item in route.children"
          :key="item.id"
          class="header__nav-dropdown-item"
        >
          <router-link
            class="header__nav-dropdown-link"
            :to="{ name: item.to }"
            >{{ item.title }}</router-link
          >
        </li>
      </ul>
      <v-icon v-if="route.children" class="header__nav-icon" size="20"
        >mdi-chevron-down</v-icon
      >
    </li>
  </ul>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';

type RouterItem = {
  id: string;
  title: string;
  to: string;
  children?: RouterItem[];
};

export default defineComponent({
  name: 'HeaderNav',
  setup() {
    const routerList = computed<RouterItem[]>(() => [
      {
        id: '1',
        title: 'Home',
        to: 'home',
      },
      {
        id: '2',
        title: 'Pages',
        to: 'home', // TODO: change when has route
        children: [],
      },
      {
        id: '3',
        title: 'Categories',
        to: 'home', // TODO: change when has route
        children: [
          {
            id: '1',
            title: 'Tips',
            to: 'home', // TODO: change when has route
          },
          {
            id: '2',
            title: 'Resources',
            to: 'home', // TODO: change when has route
          },
          {
            id: '3',
            title: 'Guides',
            to: 'home', // TODO: change when has route
          },
        ],
      },
      {
        id: '4',
        title: 'Contact',
        to: 'home', // TODO: change when has route
      },
      {
        id: '5',
        title: 'Subscribe',
        to: 'home', // TODO: change when has route
      },
    ]);

    return { routerList };
  },
});
</script>

<style lang="scss" scoped>
.header {
  &__nav {
    @include flex-box(center);

    &-item {
      position: relative;
      padding: 0 14px;

      &:hover {
        .header__nav-dropdown {
          height: auto;
          padding: 28px 32px;
          opacity: 1;
          visibility: visible;
          transition: all 0.3s ease-in-out;
        }

        .header__nav-icon {
          transform: rotate(-180deg);
        }
      }
    }

    &-link {
      @include text-link();
      text-decoration: none;
      transition: all 0.3s ease-out;

      &:hover {
        opacity: 0.7;
      }
    }

    &-icon {
      margin-left: 8px;
      transition: all 0.3s ease-out;
    }

    &-dropdown {
      @include flex-box(center, flex-start);
      flex-direction: column;
      gap: 18px;
      position: absolute;
      top: 20px;
      left: -8px;
      padding: 0 32px;
      height: 0;
      border: 1px solid $grey-1;
      border-radius: 20px;
      background-color: $white;
      box-shadow: 0 2px 12px 0 rgb(0 0 0 / 12%);
      opacity: 0;
      visibility: hidden;

      &-link {
        @include text-style(16px, 400, 20px, $secondary);
        text-decoration: none;
        transition: all 0.3s ease-in-out;

        &:hover {
          color: $primary;
        }
      }
    }
  }
}
</style>
