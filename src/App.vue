<template>
  <router-view />
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'App',
  setup() {},
});
</script>

<style lang="scss">
@import './styles/scss/reset.scss';
* {
  font-family: 'Manrope', sans-serif;
}
</style>
