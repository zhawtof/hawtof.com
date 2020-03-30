<template>
  <div></div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class EscapeHandler extends Vue {
  handleEscape(e): void {
    console.log(e);
    if (e.key === 'Esc' || e.key === 'Escape') this.$emit('escapePressed');
  }

  created(): void {
    document.addEventListener('keydown', this.handleEscape);
  }

  beforeDestroy(): void {
    document.removeEventListener('keydown', this.handleEscape);
  }
}
</script>
