<template>
  <div class="master-layout">
    <TheHeader />
    <v-container>
      <slot name="default" />
    </v-container>
    <TheFooter />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TheHeader from '@/components/TheHeader/TheHeader.vue';
import TheFooter from '@/components/TheFooter/TheFooter.vue';

export default defineComponent({
  name: 'MasterLayout',
  components: { TheHeader, TheFooter },
  setup() {},
});
</script>

<style lang="scss" scoped>
.master-layout {
  position: relative;
  width: 100vw;
  height: 100vw;
}
</style>
