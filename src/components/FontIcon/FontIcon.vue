<template>
  <v-icon :size="props.size">{{ props.name }}</v-icon>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'FontIcon',
  props: {
    size: {
      type: String,
      default: '20',
    },
    name: {
      type: String,
      default: '',
    },
  },
  setup(props) {
    return { props };
  },
});
</script>
