<template>
  <div class="nav-child">
    <div
      v-for="section in routerList"
      :key="section.id"
      class="nav-child__item"
    >
      <div class="nav-child__item-title">{{ section.title }}</div>
      <ul class="nav-child__item-list">
        <li v-for="route in section.children" :key="route.id">
          <router-link
            :class="[
              'nav-child__item-link',
              { 'nav-child__item-url': route.isHasLink },
            ]"
            :to="{ name: route.to }"
            >{{ route.title }}</router-link
          >
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';

type RouterItem = {
  id: string;
  title: string;
  children: RouterItemChildren[];
};

type RouterItemChildren = {
  id: string;
  title: string;
  to: string;
  isHasLink?: boolean;
};

export default defineComponent({
  components: {},
  name: 'HeaderNavChild',
  setup() {
    const routerList = computed<RouterItem[]>(() => [
      {
        id: '1',
        title: 'page',
        children: [
          {
            id: '1.1',
            title: 'Home',
            to: 'home', // TODO: change when has route
          },
          {
            id: '1.2',
            title: 'Home (Premium)',
            to: 'home', // TODO: change when has route
          },
          {
            id: '1.3',
            title: 'Blog Post',
            to: 'home', // TODO: change when has route
          },
          {
            id: '1.4',
            title: 'Blog Post (Premium)',
            to: 'home', // TODO: change when has route
          },
          {
            id: '1.5',
            title: 'Subscribe',
            to: 'home', // TODO: change when has route
          },
          {
            id: '1.6',
            title: 'Contact',
            to: 'home', // TODO: change when has route
          },
          {
            id: '1.7',
            title: 'Sign In',
            to: 'home', // TODO: change when has route
          },
          {
            id: '1.8',
            title: 'Sign up',
            to: 'home', // TODO: change when has route
          },
          {
            id: '1.9',
            title: 'Update password',
            to: 'home', // TODO: change when has route
          },
          {
            id: '1.10',
            title: 'Reset password',
            to: 'home', // TODO: change when has route
          },
          {
            id: '1.11',
            title: 'Access denied',
            to: 'home', // TODO: change when has route
          },
          {
            id: '1.12',
            title: 'User account',
            to: 'home', // TODO: change when has route
          },
        ],
      },
      {
        id: '2',
        title: 'Utility Pages',
        children: [
          {
            id: '2.1',
            title: 'Start here',
            to: 'home', // TODO: change when has route
          },
          {
            id: '2.2',
            title: 'Styleguide',
            to: 'home', // TODO: change when has route
          },
          {
            id: '2.3',
            title: '404 Not Found',
            to: 'home', // TODO: change when has route
          },
          {
            id: '2.4',
            title: 'Password protected',
            to: 'home', // TODO: change when has route
          },
          {
            id: '2.5',
            title: 'Licenses',
            to: 'home', // TODO: change when has route
          },
          {
            id: '2.6',
            title: 'Changelog',
            to: 'home', // TODO: change when has route
          },
          {
            id: '2.7',
            title: 'browser more templates',
            to: 'home', // TODO: change when has route
            isHasLink: true,
          },
        ],
      },
    ]);

    return { routerList };
  },
});
</script>

<style lang="scss" scoped>
.nav-child {
  @include flex-box(center, flex-start);
  gap: 30px;
  width: 460px;

  &__item {
    flex-grow: 1;
    flex-shrink: 0;

    &-title {
      @include text-style(18px, 700, 20px, $primary);
      text-transform: uppercase;
      margin-bottom: 12px;
    }

    &-list {
      @include flex-box(center, flex-start);
      flex-direction: column;
      gap: 12px;
    }

    &-link {
      @include text-style(16px, 400, 20px, $secondary);
      text-decoration: none;
      transition: all 0.3s ease-in-out;

      &:hover {
        color: $primary;
      }
    }

    &-url {
      color: $primary;
      font-weight: 600;
      text-transform: uppercase;
      padding-bottom: 4px;
      border-bottom: 2px solid $primary;
    }
  }
}
</style>
