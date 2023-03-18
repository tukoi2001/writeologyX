<template>
  <MasterLayout> Hello </MasterLayout>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import MasterLayout from '@/layouts/MasterLayout.vue';

export default defineComponent({
  name: 'HomeContainer',
  components: { MasterLayout },
  setup() {},
});
</script>

<style lang="scss" scoped></style>
