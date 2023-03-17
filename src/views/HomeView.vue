<template>
  <div class="home">
    <p>Hello</p>
    <v-icon size="20">mdi-chevron-right</v-icon>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'HomeView',
  components: {},
  setup() {},
});
</script>

<style lang="scss" scoped>
.home {
  p {
    color: $action-blue;
  }
}
</style>
