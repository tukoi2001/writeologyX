<template>
  <div class="header">
    <v-container>
      <HeaderTop />
      <HeaderNav />
    </v-container>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';
import { IMG_URL } from '@/configs/constants';
import HeaderTop from './HeaderTop/HeaderTop.vue';
import HeaderNav from './HeaderNav/HeaderNav.vue';

type IconSocial = {
  id: string;
  icon: string;
  target: string;
};

export default defineComponent({
  name: 'TheHeader',
  components: { HeaderNav, HeaderTop },
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

    return { icons, IMG_URL };
  },
});
</script>

<style lang="scss" scoped>
.header {
  padding: 48px 0;
  background-color: $white;
  border-bottom: 1px solid $grey-1;
}
</style>
