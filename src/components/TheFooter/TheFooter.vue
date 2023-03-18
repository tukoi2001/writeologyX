<template>
  <v-container>
    <div class="footer">Footer</div>
  </v-container>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'TheFooter',
  setup() {},
});
</script>

<style lang="scss" scoped>
.footer {
  @include flex-box();
}
</style>
