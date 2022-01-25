<script lang="ts">
import { defineComponent } from 'vue';
import Avatar from '@/vue-avatar-sdh.vue';

export default defineComponent({
  name: 'ServeDev',
  components: {
    Avatar
  }
});
</script>

<template>
  <div id="app">
    <Avatar username="Dr. Soumyadip Hazra" />
  </div>
</template>
